# Quiz: Ethernet LAN switching
## Quiz 1
Which field of an ethernet frame provides reciever clock synchronization?

A) Preamble
B) SFD (Start Frame Delimiter)
C) Type
D) FCS (Frame Check Sequence)

### Answer: 
A) Preamble

### Explanation:
The preamble is a series of bits (1s & 0s), 7 bytes long, which allows the recieving device to sync its recieved clock.

---

## Quiz 2
How long is the physical address (MAC address) of a network device?

A) 32 bytes
B) 32 bits
C) 48 bytes
D) 48 bits

### Answer
D) 48 bits

### Explanation
A MAC address is a unique identifier assigned to network interfaces for communications at the data link layer (Layer 2) of the OSI model. It is used to identify devices on a local network and facilitate communication between them. A MAC address is 48 bits long, which is equivalent to 6 bytes (since 1 byte = 8 bits). Therefore, the correct answer is D) 48 bits.

---

## Quiz 3
What is the OUI of this MAC address:
E8BA.7011.2874

A) E8BA
B) E8BA.70
C) 7011 
D) E8BA.7011

### Answer
B) E8BA.70

### Explanation
The OUI (Organizationally Unique Identifier) is the first 24 bits (or the first 3 bytes) of a MAC address, which identifies the manufacturer of the network device. In this case, the OUI of the MAC address E8BA.7011.2874 is E8BA.70, which corresponds to the first 3 bytes of the MAC address. Therefore, the correct answer is B) E8BA.70.

---

# Quiz 4
Which field of an ethernet frame does a switch use to populate its MAC address table?

A) Preamble
B) Length
C) Source MAC Address
D) Destination MAC Address

### Answer
C) Source MAC Address

### Explanation
A switch populates its MAC address table by examining the source MAC address of each incoming ethernet frame. This allows the switch to learn which devices are connected to which ports, enabling it to forward frames more efficiently.

---

# Quiz 5
What kind of frame does a switch flood out of all interfaces except the one it was recieved on?

A) Unknown unicast
B) Known unicast
C) Allcast
D) Broadcast

### Answer
A) Unknown unicast

### Explanation
An unknown unicast is a unicast frame whose destination MAC address is not yet in the switch’s MAC table. When a switch receives an unknown unicast frame, it floods the frame out of all interfaces except the one it was received on, in an attempt to find the destination device and learn its MAC address for future reference.

---
# Quiz 6
You send a 36-byte ping to another computer and perform a packet capture to analyse the network traffic. You notice a long series of bytes of 00000000 at the end of the Ethernet payload. How can you explain these zeros?

A) Pings are a series of zeros
B) They are padding bytes
C) They are the Ethernet FCS (Frame Check Sequence)

### Answer
B) They are padding bytes

### Explanation
Ethernet frames have a minimum payload size of 46 bytes. If the actual data being sent is less than 46 bytes, the sender adds padding bytes (which are typically zeros) to ensure that the frame meets the minimum size requirement. In this case, since the ping is only 36 bytes, 10 padding bytes (00000000) are added to reach the minimum payload size of 46 bytes. Therefore, the correct answer is B) They are padding bytes.

---
# Quiz 7
Which of these messages is sent to all hosts on the local network?

A) ARP request
B) ARP reply
C) ICMP echo request
D) ICMP echo reply

### Answer
A) ARP request

### Explanation
An ARP (Address Resolution Protocol) request is a broadcast message sent by a device to all hosts on the local network to find the MAC address associated with a specific IP address. The ARP request is sent to the broadcast MAC address (FF:FF:FF:FF:FF:FF), which ensures that all devices on the local network receive the request. In contrast, an ARP reply is sent directly to the requesting device, and ICMP echo requests and replies are typically unicast messages between two specific devices. Therefore, the correct answer is A) ARP request.

---
# Quiz 8
Which fields are present in the output of the show mac address-table command on a cisco switch?

A) MAC address, VLAN, Ports
B) VLAN, MAC address, Ports
C) VLAN, MAC address, Ports, Type
D) Internet Address, Physical Address, Type

### Answer
C) VLAN, MAC address, Ports, Type

### Explanation
The show mac address-table command on a Cisco switch displays the MAC address table, which includes the following fields: VLAN (the VLAN associated with the MAC address), MAC address (the unique identifier for the device), Ports (the switch port(s) where the MAC address is learned), and Type (indicating whether the entry is dynamic, static, or secure). Therefore, the correct answer is C) VLAN, MAC address, Ports, Type.

---
# Quiz 9
Which types of frames does a switch send out of all interfaces, except the one the frame was received on?

A) Broadcast, unknown unicast
B) Broadcast, known unicast
C) Known unicast, unknown unicast
D) Broadcast, known unicast, unknown unicast

### Answer
A) Broadcast, unknown unicast

### Explanation
A switch floods frames out of all interfaces except the one it was received on in two scenarios:
1. Broadcast frames: These are frames sent to the broadcast MAC address (FF:FF:FF:FF:FF:FF) and are intended for all devices on the local network. The switch floods these frames to ensure that all devices receive them.
2. Unknown unicast frames: These are unicast frames whose destination MAC address is not yet in the switch’s MAC table. The switch floods these frames to find the destination device and learn its MAC address for future reference.
In contrast, known unicast frames are sent only to the specific port associated with the destination MAC address in the switch’s MAC table. Therefore, the correct answer is A) Broadcast, unknown unicast.

---
# Quiz 10
Which command is used on a cisco switch to clear all dynamic MAC addresses on a specific interface from the MAC address table?

A) clear mac address-table interface interface [interface-id]
B) clear mac-address-table dynamic interface [interface-id]
C) clear mac-address table interface [interface-id]
D) clear mac address-table dynamic interface [interface-id]

### Answer
D) clear mac address-table dynamic interface [interface-id]