# Quiz: DNS
## Quiz 1
Which of the following windows command prompt commands will displat the PC's DNS server? (select two)

A) ipconfig
B) ipconfig /all
C) ipconfig /displaydns
D) nslookup

### Anwsers
Anwsers are B and D.

---

## Quiz 2
Which of the following statements about DNS are true? (select two)

A) messages greater than 512 bytes in size are sent using UDP
B) "A" records map hostnames to IPv4 addresses
C) "AAA" records map hostnames to IPv6 addresses
D) A cisco router can be configured as a DNS server and DNS client at the same time.

### Anwsers
Anwsers are B and D.

### Explanation
Two statements are true:

- **B) "A" records map hostnames to IPv4 addresses**  
  Correct — an **A record** stores a 32‑bit IPv4 address. It is the most common DNS record used for name‑to‑IP mapping.

- **D) A Cisco router can be configured as a DNS server and DNS client at the same time**  
  Correct — Cisco IOS supports both roles:  
  - As a **DNS client**, it resolves names using `ip name-server <IP>`  
  - As a **DNS server**, it can answer queries using `ip dns server`

The incorrect statements:

- **A) messages greater than 512 bytes are sent using UDP**  
  Incorrect — classic DNS uses **UDP for queries**, but if a response exceeds **512 bytes**, DNS switches to **TCP**.  
  (EDNS0 can extend UDP size, but CCNA expects the traditional rule.)

- **C) "AAA" records map hostnames to IPv6 addresses**  
  Incorrect — the correct record type is **AAAA**, not AAA.  
  AAAA records store 128‑bit IPv6 addresses.

---
## Quiz 3
PC1 is configured to use an external DNS server (8.8.8.8).  
Which DNS command is required on R1 to allow this?

A) `R1(config)#ip domain lookup`
B) `R1(config)#ip name-server 8.8.8.8 ` 
C) `R1(config)#ip dns server`
D) No DNS configurations are needed on R1.

### Answer
Answer is **D**.

### Explanation
PC1 sends DNS queries directly to **8.8.8.8**, not to R1.  
R1 only needs to **route** the packets toward the internet — it does **not** need to act as a DNS client or DNS server for this scenario.

- **A)** enables DNS lookup *on the router itself*, not needed.  
- **B)** configures R1 to use 8.8.8.8 *for its own lookups*, not needed.  
- **C)** turns R1 into a DNS server, not required.  
- **D)** is correct because R1 simply forwards traffic; no DNS configuration is required.

---
## Quiz 4
Which of the following Cisco IOS commands shows the cached name/IP address mappings learned via DNS?

A) ``R1#show hosts`
B) ``R1#show dns cache`
C) ``R1#ipconfig /displaynds`
D) ``R1#show dns hosts`

### Anwser
Anwser is A.

---
## Quiz 5
Which of the following protocols can hosts use to automatically learn the address of their DNS server?

A) DNS
B) SSH
C) DHCP
D) IP

### Anwser
Anwser is C.

### Explanation
**DHCP** provides hosts with multiple network parameters automatically, including:
  - IP address  
  - Subnet mask  
  - Default gateway  
  - **DNS server address**  
  This is delivered inside the DHCP **Offer** and **ACK** messages.

The incorrect options:

- **A) DNS**  
  DNS resolves names to IPs, but it does **not** tell a host which DNS server to use.

- **B) SSH**  
  Secure remote‑access protocol; unrelated to address configuration.

- **D) IP**  
  IP defines addressing and routing, but it does **not** distribute DNS server 

---
## Quiz 6
A web browser on HostA sends an HTTP request to WWW_server.  
This is the first time HostA has ever contacted WWW_server, and HostA does not use a hosts file.  
With which device(s) does HostA establish a TCP connection in this scenario?

A) only DNS_server and WWW_server  
B) DNS_server, Default_GW, and WWW_server  
C) only Default_GW and WWW_server  
D) only WWW_server

### Answer
Answer is **A**.

### Explanation
HostA must first resolve the domain name of WWW_server.  
Because this is the **first** request and no hosts file is used, HostA sends a DNS query to the **DNS_server**.  
DNS uses **UDP/TCP**, but the browser itself only cares about the final TCP sessions.

Two TCP connections occur:

1. **HostA → DNS_server**  
   For DNS resolution (TCP fallback possible).

2. **HostA → WWW_server**  
   The actual HTTP session is a TCP connection directly to the web server’s IP.

The **Default_GW** only forwards packets at Layer 3.  
HostA does **not** establish a TCP session with the gateway.

