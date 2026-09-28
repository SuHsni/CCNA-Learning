# ARP, ICMP, and MAC Learning in Cisco Packet Tracer

## Scenario

We have a LAN using the `172.16.16.0/24` network:

| Device   | IP Address     | MAC Address      | Port  |
| -------- | -------------- | ---------------- | ----- |
| PC0      | `172.16.16.10` | `0007.ECE9.4A40` | Fa0/1 |
| Laptop0  | `172.16.16.11` | `0007.EC78.6005` | Fa0/2 |
| Printer  | `172.16.16.12` | —                | Fa0/3 |
| IP Phone | `172.16.16.13` | —                | Fa0/4 |
| Server   | `172.16.16.14` | —                | Gi0/1 |

PC0 runs:

```cmd
ping 172.16.16.11
```

---

## Step 1: ARP Request

PC0 knows Laptop0's IP address but does not know its MAC address.

Therefore, PC0 sends an **ARP Request** as an Ethernet Broadcast:

```text
Source MAC      = 0007.ECE9.4A40
Destination MAC = FFFF.FFFF.FFFF
Target IP       = 172.16.16.11
```

The message basically means:

> “Who has 172.16.16.11? Tell me your MAC address.”

---

## Step 2: Switch Learns PC0's MAC

The switch receives the frame on **Fa0/1** and learns:

| MAC Address      | Port  | Type    |
| ---------------- | ----- | ------- |
| `0007.ECE9.4A40` | Fa0/1 | Dynamic |

Because the destination is Broadcast, the switch **floods** the frame to the other ports in the same VLAN.

---

## Step 3: Why Does Only Laptop0 Reply?

All devices receive the Broadcast, but they compare the ARP **Target IP** with their own IP address.

- Printer: `172.16.16.12` ≠ `172.16.16.11` → No reply
- IP Phone: `172.16.16.13` ≠ `172.16.16.11` → No reply
- Server: `172.16.16.14` ≠ `172.16.16.11` → No reply
- **Laptop0: `172.16.16.11` = `172.16.16.11` → ARP Reply** ✅

Laptop0 sends an **ARP Reply** back to PC0 as a Unicast:

```text
Source MAC      = 0007.EC78.6005
Destination MAC = 0007.ECE9.4A40
```

The important point is:

> **ARP Request is Broadcast, but only the device that owns the Target IP responds.**

---

## Step 4: Switch Learns Laptop0's MAC

The switch receives the ARP Reply on Fa0/2 and learns:

| MAC Address      | Port  | Type    |
| ---------------- | ----- | ------- |
| `0007.ECE9.4A40` | Fa0/1 | Dynamic |
| `0007.EC78.6005` | Fa0/2 | Dynamic |

Because the destination MAC is already known, the switch forwards the reply directly to **Fa0/1**.

---

## Step 5: ICMP Ping

PC0 now has the mapping:

```text
172.16.16.11 → 0007.EC78.6005
```

So it can send the ICMP Echo Request directly to Laptop0.

The sequence is:

```text
ARP Request
     ↓
ARP Reply
     ↓
ICMP Echo Request
     ↓
ICMP Echo Reply
```

---

## Key CCNA Points

### Switch Operations

- **Learning:** Source MAC → Incoming Port
- **Flooding:** Broadcast/unknown destination → multiple ports
- **Forwarding:** Known destination MAC → specific port

### ARP

- ARP Request → **Broadcast**
- ARP Reply → **Unicast**
- ARP maps **IP → MAC**

### MAC Table

The switch learns a MAC address from the **Source MAC of an incoming frame**.

Therefore, Printer, IP Phone, and Server do not appear in the MAC table simply because they received the Broadcast. They would be learned when they send a frame to the switch.

### ARP Table vs. MAC Table

```text
ARP Table:
IP Address → MAC Address

MAC Table:
MAC Address → Switch Port
```

**Main concept:** The switch distributes the ARP Broadcast, but only the device whose IP matches the ARP Target IP sends a reply.
