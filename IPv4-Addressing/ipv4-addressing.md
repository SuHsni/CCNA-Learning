### EX 1

## IP Add: 10.10.10.10/8

- Class ?
- Network ID?
- First Valid IP Add?
- Last Valid IP Add?
- Broadcast Add?
- Maximum Usable Hosts?

---

10.10.10.10 => Binary => 00001010.00001010.00001010.00001010

---

Default Subnet Mask: 255.0.0.0 => Class A

255.0.0.0 => Binary =>
11111111.00000000.00000000.00000000

network . host . host . host

---

Network ID => IP Add AND Subnetmask :

00001010.00001010.00001010.00001010
AND
11111111.00000000.00000000.00000000

Result:
00001010.00000000.00000000.00000000
Decimal => 10.0.0.0

---

First Valid IP Add =>
00001010.00000000.00000000.00000001 => Decimal => 10.0.0.1

---

Last Valid IP Add =>
00001010.11111111.11111111.11111110 => Decimal => 10.255.255.254

---

Broadcast Add =>
00001010.11111111.11111111.11111111 => Decimal => 10.255.255.255

---

Maximum Usable Hosts? 2^H - 2 = 2^24 - 2

### EX 2

## IP Add: 172.16.1.10/16

- Class ?
- Network ID?
- First Valid IP Add?
- Last Valid IP Add?
- Broadcast Add?
- Maximum Usable Hosts?

---

172.16.1.10 => Binary => 10101100.00010000.00000001.00001010

---

Default Subnet Mask: 255.255.0.0 => Class B

255.255.0.0 => Binary =>
11111111.11111111.00000000.00000000

network . network . host . host

---

Network ID => IP Add AND Subnetmask :

10101100.00010000.00000001.00001010
AND
11111111.11111111.00000000.00000000

Result:
10101100.00010000.00000000.00000000
Decimal => 172.16.0.0

---

First Valid IP Add =>
10101100.00010000.00000000.00000001 => Decimal => 172.16.0.1

---

Last Valid IP Add =>
10101100.00010000.11111111.11111110 => Decimal => 172.16.255.254

---

Broadcast Add =>
10101100.00010000.11111111.11111111 => Decimal => 172.16.255.255

---

Maximum Usable Hosts? 2^H - 2 = 2^16 - 2

### EX 3

## IP Add: 192.168.1.12/24

- Class ?
- Network ID?
- First Valid IP Add?
- Last Valid IP Add?
- Broadcast Add?
- Maximum Usable Hosts?

---

192.168.1.12 => Binary => 11000000.10101000.00000001.00001100

---

Default Subnet Mask: 255.255.255.0 => Class C

255.255.255.0 => Binary =>
11111111.11111111.11111111.00000000

network . network . network . host

---

Network ID => IP Add AND Subnetmask :

11000000.10101000.00000001.00001100
AND
11111111.11111111.11111111.00000000

Result:
11000000.10101000.00000001.00000000
Decimal => 192.168.1.0

---

First Valid IP Add =>
11000000.10101000.00000001.00000001 => Decimal => 192.168.1.1

---

Last Valid IP Add =>
11000000.10101000.00000001.11111110 => Decimal => 192.168.1.254

---

Broadcast Add =>
11000000.10101000.00000001.11111111 => Decimal => 192.168.1.255

---

Maximum Usable Hosts? 2^H - 2 = 2^8 - 2
