# OSI model
Copyright © Lukas Van der Spiegel (author)

Focus on the trajectory for software engineering.  
These notes are written at **professional bachelor level** in applied computer science.  
They intentionally avoid deep CCNA‑exam knowledge.

---
## What it is
The OSI model is a conceptual framework that describes how data moves across a network.
It divides networking into 7 layers, each with a clear role.
You only need to understand what each layer does, why it exists, and how it helps troubleshooting.

The OSI model is not something you configure — it is a mental model to understand communication.

## Why it matters
- Helps you understand where a problem is happening
- Helps you explain how data travels through a network
- Helps you separate application issues from network issues
- Helps you understand switches (Layer 2) and routers (Layer 3)

Examples:
- Broken cable → Layer 1
- Wrong MAC address → Layer 2
- Wrong IP address → Layer 3
- Application bug → Layer 7

## The 7 Layers
### Layer 7 — Application
**The layer closest to the user.**
Provides network services to applications.

Examples:
HTTP, HTTPS, DNS, SMTP

Think: “What the user interacts with.”

### Layer 6 — Presentation
**Makes sure data is in a format both sides understand.**

Functions:
- Encryption (TLS/SSL)
- Compression
- Data formatting (e.g., text, images)

Think: “Translate and secure the data.”

### Layer 5 — Session
**Creates, manages, and ends communication sessions.**

Examples:
- Logging into a server
- Video call session
- Remote desktop session

Think: “Start, maintain, end the conversation.”

### Layer 4 — Transport
**Responsible for end‑to‑end delivery between devices.**

Two main protocols:
- TCP — reliable
- UDP — fast, no reliability

Also uses port numbers (e.g., HTTP = 80, HTTPS = 443).

Think: “Deliver the data correctly to the right application.”

### Layer 3 — Network
**Responsible for IP addressing and routing between networks.**

Examples:
- IP
- Routers
- ICMP (ping)

Think: “Find the best path to the destination.”

### Layer 2 — Data Link
**Responsible for communication inside the same local network.**

Uses MAC addresses.
Switches operate here.

Examples:
- Ethernet
- Wi‑Fi
- ARP

Think: “Deliver the frame to the correct device in the LAN.”

### Layer 1 — Physical
**Responsible for sending bits (0s and 1s) over the medium.**

Examples:
- UTP cables
- Fiber
- Electrical signals
- Wireless radio waves

Think: “The actual physical connection.”

