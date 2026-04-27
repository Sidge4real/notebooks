# IPv4 Adressing

- **Jeremy's IT Lab** — [Video](https://www.youtube.com/watch?v=3ROdsfEUuhs)

---
## What is an IPv4 Address?
An **IPv4 address** is a **logical Layer‑3 address** used to identify devices across different networks.  
It enables **routing**, **path selection**, and **communication between hosts on different LANs**.

- Written in **dotted‑decimal notation**
- Consists of **4 octets** → each **8 bits** → total **32 bits**
- Each octet ranges from **0–255**
- Used by routers to forward packets between networks

Example: **192.168.1.254**

## Dotted Decimal & Binary
IPv4 addresses can be represented in:
- **Dotted decimal** (human‑friendly)
- **Binary** (router‑friendly)

Example:  
192 → `11000000`  
168 → `10101000`  
1 → `00000001`  
254 → `11111110`

Binary is essential for:
- Subnetting
- Determining network/host boundaries
- Calculating network & broadcast addresses

## Network Portion vs Host Portion
An IPv4 address is split into:
- **Network portion** → identifies the network
- **Host portion** → identifies a device within that network

The **subnet mask** or **prefix length** determines where the split occurs.

Example:  
`192.168.1.254 /24`  
- Network: first 24 bits  
- Host: last 8 bits  

## IPv4 Address Classes 
(Legacy Concept)
Classes are mostly historical but still appear in CCNA theory.

| Class | Range | Default Mask | Notes |
|------|--------|--------------|-------|
| A | 0.0.0.0 – 127.255.255.255 | /8 | Very large networks |
| B | 128.0.0.0 – 191.255.255.255 | /16 | Medium networks |
| C | 192.0.0.0 – 223.255.255.255 | /24 | Small networks |
| D | 224.0.0.0 – 239.255.255.255 | N/A | Multicast |
| E | 240.0.0.0 – 255.255.255.255 | N/A | Experimental |

Modern networks use **CIDR**, not classes.

## Prefix Lengths / Subnet Masks
The **prefix length** (e.g., `/24`) tells how many bits belong to the network portion.

Examples:
- `/8` → 255.0.0.0  
- `/16` → 255.255.0.0  
- `/24` → 255.255.255.0  

Subnet masks allow:
- Splitting networks into smaller subnets  
- Controlling host capacity  
- Efficient IP allocation  

## Network Address & Broadcast Address
Every IPv4 subnet has two special addresses:

### **Network Address**
- All host bits = **0**
- Identifies the subnet itself  
Example `/24`:  
`192.168.1.0`

### **Broadcast Address**
- All host bits = **1**
- Used to send to all hosts in the subnet  
Example `/24`:  
`192.168.1.255`

Routers **do not forward** broadcast traffic.

## Why IPv4 Addressing Matters (CCNA)
You must be able to:
- Convert between decimal and binary  
- Identify network/host portions  
- Determine valid host ranges  
- Calculate network & broadcast addresses  
- Understand prefix lengths  
- Recognize address classes  
- Perform subnetting quickly  

These skills are essential for routing, switching, and troubleshooting.

---

## Example Breakdown
IPv4 Address: **192.168.10.25 /24**

Binary:
- 192 → `11000000`
- 168 → `10101000`
- 10 → `00001010`
- 25 → `00011001`

Network address: **192.168.10.0**  
Broadcast address: **192.168.10.255**  
Host range: **192.168.10.1 – 192.168.10.254**  
Total hosts: **254**

---

## Max Hosts per Subnet
The number of usable hosts in a subnet is determined by the number of **host bits**.

Formula:  
**Hosts = 2^(number of host bits) – 2**  
(–2 for the network and broadcast addresses)

Examples:  
- `/24` → 8 host bits → 2⁸ – 2 = **254 hosts**  
- `/25` → 7 host bits → 2⁷ – 2 = **126 hosts**  
- `/30` → 2 host bits → 2² – 2 = **2 hosts** (point‑to‑point links)

Calculation is /24 → 32 - 24 = 8 host bits!

## Calculating the Network Address
The **network address** is the address where **all host bits = 0**.

Steps:
1. Convert the IP address to binary  
2. Set all host bits to 0  
3. Convert back to decimal

Example:  
`192.168.10.25 /24`  
Host bits = last 8 bits → all 0  
→ **192.168.10.0**

## Calculating the Broadcast Address
The **broadcast address** is the address where **all host bits = 1**.

Example `/24`:  
Host bits = last 8 bits → all 1  
→ **192.168.10.255**

## First & Last Usable Host
Every subnet has two reserved addresses:

- **Network address** → not usable  
- **Broadcast address** → not usable  

Therefore:

- **First usable** = network address + 1  
- **Last usable** = broadcast address – 1  

Example `/24`:  
- Network: 192.168.10.0  
- First usable: **192.168.10.1**  
- Last usable: **192.168.10.254**  
- Broadcast: 192.168.10.255  

## Identifying and Calculating Subnets
Important for CCNA:

- Recognize which subnet size corresponds to which prefix  
- Determine which subnet an IP address belongs to  
- Calculate:  
  - network address  
  - broadcast address  
  - host range  
  - number of hosts  

Example `/26` (64 addresses per subnet):  
Subnets:  
- 192.168.1.0 – 63  
- 192.168.1.64 – 127  
- 192.168.1.128 – 191  
- 192.168.1.192 – 255  

IP: **192.168.1.130** belongs to:  
→ **192.168.1.128/26**  
Network: 128  
Broadcast: 191  
Hosts: 129–190  

## IPv4 Address Classes (Clarification)
Jeremy emphasizes that classes are **legacy**, but still useful for recognition:

- Class A → first bit = 0  
- Class B → first bits = 10  
- Class C → first bits = 110  
- Class D → multicast  
- Class E → experimental  

Modern networks use **CIDR**, not classful addressing.

## IP Configuration on Cisco Devices

### Configure an interface
```
enable
configure terminal
interface GigabitEthernet0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
```

### Show IP information
```
show ip interface brief
show running-config
```

### Default gateway on a switch
```
ip default-gateway 192.168.10.1
```

### Test connectivity
```
ping 192.168.10.254
```

### Important for CCNA
- Routers use **Layer 3 interfaces**  
- Switches use **SVIs** (e.g., `interface vlan 1`)  
- Subnetting must be applied correctly to assign valid IPs to interfaces  