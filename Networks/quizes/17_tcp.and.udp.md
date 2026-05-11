# Quiz: TCP and UDP
## Quiz 1
Which of the follwing is well-known port number as defined by IANA?

A) 1010
B) 2001
C) 4023
D) 65000

### Anwser
Anwser is A.
### Explanation
Ranges are set as following by IANA:
- Well-known port numbers: 0 - 1023
- Registered port numbers: 1024 - 49151
- Ephemeral/private/dynamic port numbers: 49152 - 65535

---

## Quiz 2
According to IANA specs, what range of port numbers should hosts select from when randomly selecting a source L4 port nr?

A) well-known
B) registered
C) ephemeral
D) reserved

### Anwser
Anwser is C.

### Explanation
Ranges are set as following by IANA:
- Well-known port numbers: 0 - 1023
- Registered port numbers: 1024 - 49151
- Ephemeral/private/dynamic port numbers: 49152 - 65535

When a client initiates a connection (for example, to TCP port 80 on a server), it must choose a **unique source port** so the session can be identified using the 4‑tuple:

```
Source IP  
Source Port  
Destination IP  
Destination Port
```

To avoid conflicts with well‑known or registered ports (which they never random take), the client selects from the **ephemeral range**

---

## Quiz 3
Which of the follwing are features of TCP but not UDP? (select three)

A) L4 addressing
B) Error recovery
C) Session multiplexing
D) Flow control
E) Sequencing

### Anwser
Anwsers are B, D and E

---

## Quiz 4
Which of the following Application Layer protocols use TCP to provide reliable communications? (select three)

A) SMTP
B) SNMP
C) HTTPS
D) DHCP
E) Syslog
F) SSH

### Anwser
Anwsers are A, C and F

### Explanation
Application Layer protocols choose TCP or UDP depending on whether they need **reliability**, **ordering**, and **flow control**.  
TCP provides all three, so protocols that require guaranteed delivery use it.

The following protocols in the list use **TCP**:

- **SMTP** (port 25)  
  Email transfer must be reliable — losing messages is unacceptable.

- **HTTPS** (port 443)  
  Secure web traffic requires ordered, reliable delivery.

- **SSH** (port 22)  
  Remote terminal sessions cannot tolerate dropped or unordered data.

The others do **not** use TCP:
- **SNMP** → primarily UDP (fast, lightweight)  
- **DHCP** → UDP (broadcast‑based)  
- **Syslog** → UDP by default (speed over reliability)

---

## Quiz 5
PC1 and SRV1 have an active TCP connection. SRV1 receives a TCP segment from PC1 with a sequence number of 27. When SRV1 acknowledges the segment, what will the value of the acknowledgment field in the TCP header be? Assume a TCP window size of 1.

A) 26
B) 27
C) 28

### Anwser
Anwser is C.

### Explanation

TCP uses **forward acknowledgments**: the ACK number always indicates **the next byte the receiver expects**.

If SRV1 receives a segment with:

- **Sequence number = 27**
- **Window size = 1** (meaning the segment carries exactly 1 byte of data)

…then SRV1 has successfully received byte **27** and now expects byte **28** next.

Therefore, the acknowledgment number it sends back is:

```
Ack = 28
```

---
## Quiz 6
Match each Application Layer protocol with the correct Transport Layer protocol.

**Which protocols use TCP, which use UDP, and which use both?**

Options:
- DNS  
- DHCP  
- FTP  
- HTTP  
- SMTP  
- SNMP  
- TFTP  

### Answers
**TCP:** FTP, HTTP, SMTP  
**UDP:** DHCP, SNMP, TFTP  
**TCP & UDP:** DNS

### Explanation
Different Application Layer protocols rely on different Transport Layer protocols depending on their needs:

- **TCP** is used by protocols that require reliability, ordering, and guaranteed delivery (FTP, HTTP, SMTP).  
- **UDP** is used by lightweight, fast, or broadcast‑based protocols (DHCP, SNMP, TFTP).  
- **DNS** uses **both**:  
  - UDP for fast, simple queries  
  - TCP for zone transfers or large responses

All protocols in the list map cleanly into one of these three categories.
