# Network Devices
Copyright © Lukas Van der Spiegel (author)

Focus on the trajectory for software engineering.  
These notes are written at **professional bachelor level** in applied computer science.  
They intentionally avoid deep CCNA‑exam knowledge.

---
## Network
A network is a setup where two or more devices can communicate with each other by sending and receiving digital data.
This communication can happen over an Ethernet cable, Wi‑Fi, fiber, or any other physical medium.

## Elements
A network exist of 3 basic elements:
- Devices (e.g. PC's, laptops, servers, routers, switches, ...)
- A communication medium (e.g. ethernet cable)
- A shared set of rules (protocols), so both devices can understand each other.

Devices are called **"nodes"** in a network.
A node is any device in a network that can send or receive information.

### Devices
![Device icons](./devices.icons.png)

- **Endhosts** (e.g. PC, Laptop, Server, Phone, Printer, ...)
These are the “normal” devices people use. They create and receive the actual messages.
- **Switches**
A switch is like a smart power strip for network cables. It connects many devices and makes sure each message goes to the right one.
- **Routers**
A router is like a mailman. It sends messages from your network to other networks (like the internet) and knows which way to go.
- **Firewalls**
A firewall is like a security guard. It checks every message and blocks anything unsafe.

> Connect a switch from network 1 to network 2, those networks cannot send messages towards eachother. A switch cannot communicate with another network, that's the job of a router.

### Endhosts
Enhosts are split in 2 groups:
- Server (providing a service for a client)
- Client (requesting a service from the server)

A laptop can be a server aswell if 2 computers are communicating. PC1 request a service from PC2, than PC2 is the server and PC1 the client.

### Routers

Allows communication to happen between multiple networks.
> Have fewer network interfaces/ports than switches 
(usually 2-4 ports)

> Often include additional features such as firewall protection, network address translation (NAT), and virtual private network (VPN) support


### Firewall
A firewall is like a security guard for a computer or a network.
It checks every message that comes in or goes out and decides if it’s allowed or blocked.

> can be configured to allow or block specific types of traffic based on factors such as source/destination IP address, port number, protocol, and content.

> Are known as 'Next-generation Firewalls' (NGFW) when they include advanced features such as intrusion prevention, application control, deep packet inspection and advanced filtering capabilities.

### Switch
Allows connectivity between hosts within a local area network (LAN).

> Have many network interfaces/ports for end hosts to connect to (usually 4, 8, 16, 24, or 48 ports)

#### Host-based Firewall
A host‑based firewall lives on one device (like a PC or laptop).
It protects that single device from bad or unwanted traffic.

#### Network-based Firewall
A network‑based firewall sits between the whole network and the outside world.
It protects all devices behind it at the same time.