# Small Office Structured Cabling

I built this small project in **Cisco Packet Tracer** out of curiosity and to get familiar with the **passive side of networking**.

The goal was not to build a production-ready network, but to understand how a small office network is physically wired and organized.

---

## What I Built

The project represents a small office with:

- 2 office areas
- 1 network room
- 6 PCs
- 1 network printer
- 1 access point
- 2 wall mounts / wall outlets
- 1 patch panel
- 1 network rack
- 1 Cisco 2960 switch

---

# What I Learned

## 1. Understanding the Physical Network

First, I learned that a network is not simply:

```text
PC ─────── Switch
```

In a real office, there can be several physical stages between an endpoint and the network switch.

The basic structure I learned was:

```text
End Device
    ↓
Wall Jack
    ↓
Permanent Cable
    ↓
Patch Panel
    ↓
Patch Cord
    ↓
Switch
```

This helped me understand the difference between the **physical infrastructure** and the active networking equipment.

---

## 2. Wall Jack

I used two Wall Mounts:

```text
WO-01
WO-02
```

Each one represents a network outlet in an office.

For example:

```text
PC-01
  ↓
WO-01 Jack 1
```

### What I learned

The user normally connects to the network through a **wall jack**, rather than running a permanent cable directly from the PC to the network room.

---

## 3. Punch Down

The Wall Mounts and Patch Panel both have **Punch Down** connections.

I used these connections for the permanent cables between the office and the network room.

For example:

```text
WO-01 Punch Down 1
        ↓
PP-01 Punch Down 1
```

### What I learned

A Punch Down connection is used to **terminate the individual wires of a permanent network cable**.

It is not a network device and it does not process network traffic.

---

## 4. Permanent Cabling

I then connected the Punch Down points between the offices and the Patch Panel.

For example:

```text
WO-01 Punch Down 1
        │
        │ Permanent Cable
        │
        ▼
PP-01 Punch Down 1
```

### What I learned

The permanent cable represents the structured cabling installed through the building, such as cables running through walls, ceilings, or cable pathways.

This cable is not normally something that is constantly unplugged and moved.

---

## 5. Patch Panel

I added a Patch Panel named:

```text
PP-01
```

The permanent cables from the offices terminate on the Patch Panel.

For example:

```text
Office
  │
  │ Permanent Cable
  ↓
PP-01 Punch Down
  │
  ↓
PP-01 Jack
```

### What I learned

A Patch Panel is a **passive termination and organization point**.

It does not switch packets or provide network connectivity by itself.

Its main purpose is to provide a clean and manageable place where the building's permanent cabling can be terminated and organized.

---

## 6. Patch Cord

The Patch Panel is connected to the switch using short patch cables.

For example:

```text
PP-01 Jack 1
      │
      │ Patch Cord
      ▼
SW-01 Fa0/1
```

### What I learned

A **Patch Cord** is a short, usually pre-terminated network cable used to connect equipment or ports together.

This is different from the permanent cable running through the building.

---

## 7. Network Rack

I placed the Patch Panel and Switch inside:

```text
RACK-01
```

### What I learned

A network rack provides a centralized place for network equipment and cabling.

In a real installation, equipment such as patch panels, switches, cable management, and other network components can be mounted and organized inside the rack.

---

## 8. Cable Management

I also learned that physical organization is an important part of structured cabling.

Cable management does not carry or process network traffic.

Its purpose is to:

- Keep cables organized
- Maintain clean cable paths
- Make troubleshooting easier
- Make equipment easier to access
- Prevent unnecessary cable clutter

In my Packet Tracer version, a dedicated **Cable Management** device was not available, so I used Packet Tracer's **Manage All Cables** option to organize the cables.

---

# Complete Connection Model

The final physical model I built can be summarized as:

```text
PC / Printer / AP
       │
       │ Patch Cord
       ▼
   Wall Jack
       │
       │ Permanent Cable
       ▼
   Punch Down
       │
       ▼
   Patch Panel
       │
       │ Patch Cord
       ▼
     Switch
```

---

# Port Mapping

I also practiced documenting the physical connections instead of simply connecting cables randomly.

| Endpoint   | Wall Jack | PP Punch Down | PP Jack | Switch Port |
| ---------- | --------- | ------------- | ------- | ----------- |
| PC-01      | WO-01/1   | PP-01/1       | Jack 1  | Fa0/1       |
| PC-02      | WO-01/2   | PP-01/2       | Jack 2  | Fa0/2       |
| PC-03      | WO-01/3   | PP-01/3       | Jack 3  | Fa0/3       |
| PRINTER-01 | WO-01/4   | PP-01/7       | Jack 7  | Fa0/7       |
| PC-04      | WO-02/1   | PP-01/4       | Jack 4  | Fa0/4       |
| PC-05      | WO-02/2   | PP-01/5       | Jack 5  | Fa0/5       |
| PC-06      | WO-02/3   | PP-01/6       | Jack 6  | Fa0/6       |
| AP-01      | WO-02/4   | PP-01/8       | Jack 8  | Fa0/8       |

This mapping helped me understand how an endpoint in an office can be traced all the way back to a specific switch port.

---

# Final Takeaway

The main thing I learned from this project was that structured cabling is more than just connecting cables.

I learned the role of each part:

```text
Wall Jack
    ↓
Where the user connects

Permanent Cable
    ↓
Fixed cabling through the building

Punch Down
    ↓
Where the permanent cable is terminated

Patch Panel
    ↓
Centralized organization point

Patch Cord
    ↓
Short cable used for equipment connections

Switch
    ↓
Active device that actually forwards network traffic
```

This project gave me a basic practical understanding of the **physical layer and structured cabling** before moving further into active networking and CCNA concepts.

---

## Project File

```text
small-office-structured-cabling.pkt
```

**Tool:** Cisco Packet Tracer

**Focus:** Passive Networking / Structured Cabling / CCNA Fundamentals
