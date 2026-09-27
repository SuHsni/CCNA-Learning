# VLSM Exercise

## Problem

In this exercise, I will subnet the `192.168.0.0/16` network using **VLSM (Variable Length Subnetting)**.

I need to divide the available address space into multiple subnets based on the following host requirements:

| Subnet   | Required Hosts |
| -------- | -------------: |
| Subnet A |            500 |
| Subnet B |            250 |
| Subnet C |             32 |
| Subnet D |             64 |
| Subnet E |             32 |

## Objectives

- Calculate the appropriate subnet size for each requirement.
- Divide `192.168.0.0/16` using VLSM.
- Assign a suitable subnet to each requirement.
- Determine the following for each subnet:
  - Network ID
  - First Valid IP
  - Last Valid IP
  - Broadcast Address
  - Usable Hosts
- Use the available IP address space as efficiently as possible.

---

# Solution

First, I sorted the subnets from largest to smallest.

**Subnet A** → 500 hosts

**Subnet B** → 250 hosts

**Subnet D** → 63 hosts

**Subnet C** → 32 hosts

**Subnet E** → 32 hosts

**Subnet F** → 2 hosts

**Subnet G** → 2 hosts

**Subnet H** → 2 hosts

`192.168.0.0/16`

`128 64 32 16 8 4 2 1`

`XXXXXXXX.XXXXXXXX.XXXXXXXX.XXXXXXXX`

`11000000.10101000.00000000.00000000`

---

## Subnet A → 500

`2^9 - 2 = 510`

`192.168.0.0 : 11000000.10101000.0000000 | 0.00000000`

**NetID:** `192.168.0.0/23`

**First Valid IP:** `192.168.0.1`

**Last Valid IP:** `192.168.1.254`

**Broadcast:** `192.168.1.255`

---

## Subnet B → 250

`2^8 - 2 = 254`

`192.168.2.0 : 11000000.10101000.00000010 | .00000000`

**NetID:** `192.168.2.0/24`

**First Valid IP:** `192.168.2.1`

**Last Valid IP:** `192.168.2.254`

**Broadcast:** `192.168.2.255`

---

## Subnet D → 63

`2^7 - 2 = 126`

`192.168.3.0 : 11000000.10101000.00000011.0 | 0000000`

**NetID:** `192.168.3.0/25`

**First Valid IP:** `192.168.3.1`

**Last Valid IP:** `192.168.3.126`

**Broadcast:** `192.168.3.127`

---

## Subnet C → 32

`2^6 - 2 = 62`

`192.168.3.128 : 11000000.10101000.00000011.10 | 000000`

**NetID:** `192.168.3.128/26`

**First Valid IP:** `192.168.3.129`

**Last Valid IP:** `192.168.3.190`

**Broadcast:** `192.168.3.191`

---

## Subnet E → 32

`2^6 - 2 = 62`

`192.168.3.192 : 11000000.10101000.00000011.11 | 000000`

**NetID:** `192.168.3.192/26`

**First Valid IP:** `192.168.3.193`

**Last Valid IP:** `192.168.3.254`

**Broadcast:** `192.168.3.255`

---

## Subnet F → 2

`2^2 - 2 = 2`

`192.168.4.0 : 11000000.10101000.00000100.000000 | 00`

**NetID:** `192.168.4.0/30`

**First Valid IP:** `192.168.4.1`

**Last Valid IP:** `192.168.4.2`

**Broadcast:** `192.168.4.3`

---

## Subnet G → 2

`2^2 - 2 = 2`

`192.168.4.4 : 11000000.10101000.00000100.000001 | 00`

**NetID:** `192.168.4.4/30`

**First Valid IP:** `192.168.4.5`

**Last Valid IP:** `192.168.4.6`

**Broadcast:** `192.168.4.7`

---

## Subnet H → 2

`2^2 - 2 = 2`

`192.168.4.8 : 11000000.10101000.00000100.000010 | 00`

**NetID:** `192.168.4.8/30`

**First Valid IP:** `192.168.4.9`

**Last Valid IP:** `192.168.4.10`

**Broadcast:** `192.168.4.11`

---

# Finish :)))
