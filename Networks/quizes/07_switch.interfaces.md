# Quiz: Switch interfaces
## Quiz 1
There is a duplex mismatch between SW1's F0/1 interface and SW2's F0/1 interface, which are connected. Autonegotiation is disabled. What will be the result?

A. Improved performance
B. Collisions will occur
C. SW1 will sense SW2 duplex setting and adjust to match

### Anwser
Anwser is B.

### Explaination
A **duplex mismatch** happens when one side of a link is set to **full duplex** and the other side is set to **half duplex**.

Because **autonegotiation is disabled**, neither switch can detect or adjust to the other’s duplex mode.  
This guarantees a mismatch if the settings differ.

Effects of a duplex mismatch:

- The **half‑duplex side** uses CSMA/CD → it expects collisions  
- The **full‑duplex side** does *not* expect collisions  
- When both transmit at the same time → **late collisions**, CRC errors, frame errors  
- Severe performance degradation

Therefore:

- **A (Improved performance)** → impossible  
- **C (Sense and adjust)** → impossible without autonegotiation  
- **B (Collisions will occur)** → correct

---
## Quiz 2
What is used on half-duplex interfaces to detect and avoid collisions?

A. CSMA/CD
B. CSMA/CA
C. Autonegotiation
D. Duplex Auto

### Anwser
Anwser is A.

### Explaination
Half‑duplex Ethernet uses **CSMA/CD (Carrier Sense Multiple Access with Collision Detection)** to manage access to the shared medium.

- Devices **listen** before transmitting  
- If two devices transmit at the same time → **collision**  
- The collision is **detected**  
- A **jam signal** is sent  
- Devices wait a **random backoff time** before retrying  

This mechanism only exists in **half‑duplex** networks (e.g., hubs, duplex mismatches).

**CSMA/CA** is used in Wi‑Fi, not Ethernet.  
**Autonegotiation** has nothing to do with collision detection.

Table of comparison *(gemini generated)*

| Feature | CSMA/CD | CSMA/CA |
|--------|---------|---------|
| Full name | Carrier Sense Multiple Access with **Collision Detection** | Carrier Sense Multiple Access with **Collision Avoidance** |
| Used in | **Wired Ethernet (half‑duplex)** | **Wireless networks (Wi‑Fi)** |
| Purpose | Detect collisions after they occur | Avoid collisions before they occur |
| How it works | Device listens → sends → detects collision → sends jam signal → random backoff | Device listens → waits → may send RTS/CTS → transmits only when safe |
| Collision handling | **Detects** collisions | **Prevents** collisions |
| Typical environment | Hubs, duplex mismatches, old Ethernet | WLANs where devices cannot detect collisions |
| Duplex mode | Only in **half duplex** | Not related to duplex (Wi‑Fi is always half‑duplex by nature) |
| Still used today? | No (modern Ethernet uses switches + full duplex) | Yes (Wi‑Fi still relies on CSMA/CA) |

---
## Quiz 3
Which command shows various counters of errors detected on an interface?

A. show interfaces
B. show ip interface brief
C. show interfaces status
D. show interfaces errors

### Anwser
anwser is A.

### Explaination
The **show interfaces** command displays the full detailed interface statistics, including all error counters such as:

- Runts  
- Giants  
- CRC errors  
- Frame errors  
- Input errors  
- Output errors  
- Collisions  
- Late collisions  
- Overruns / underruns  

This is the primary command used in troubleshooting physical‑layer and data‑link‑layer issues.

Why the other options are incorrect:

- **B. show ip interface brief**  
  Only shows interface status (up/down) and IP addresses — **no error counters**.

- **C. show interfaces status**  
  Shows speed, duplex, VLAN, and port state — **no detailed errors**.

- **D. show interfaces errors**  
  This command **does not exist** in Cisco IOS.

Therefore, **A** is the only correct answer.

---
## Quiz 4
Which are examples of errors that might occur on a network interface?

A. Runts, Giants, Broadcasts
B. Shorts, Longs, Oversizes
C. Packets Bytes, Inputs, Outpunts
D. Runts, Giants, CRC

### Anwser
anwser is D.

### Explaination
Network interface error counters track **physical‑layer and data‑link‑layer problems** on an Ethernet interface.  
The most common real errors you will see on Cisco devices include:

- **Runts** → frames smaller than 64 bytes (often collisions or duplex mismatch)  
- **Giants** → frames larger than the maximum allowed size  
- **CRC errors** → corrupted frames that fail the checksum  

These are true **error conditions** and appear in `show interfaces`.

Why the other answers are incorrect:

- **A. Broadcasts**  
  Broadcasts are normal Ethernet traffic, **not errors**.

- **B. Shorts, Longs, Oversizes**  
  These terms are not standard Cisco interface error counters.

- **C. Packets, Bytes, Inputs, Outputs**  
  These are **statistics**, not errors.

Therefore, **D** is the only option that lists real interface errors you must recognize for the CCNA.

---
## Quiz 5
SW1 is trying to autonegotiate interface speed settings with SW2. However, autonegotiation is disabled on SW2’s interface.  
SW2’s interface is configured with a speed of **100 Mbps** and **full duplex**.  
What speed and duplex settings will SW1 use, assuming it succeeds in sensing the speed?

A. Speed: 100 Mbps, Duplex: Full  
B. Speed: 100 Mbps, Duplex: Half  
C. Speed: 10 Mbps, Duplex: Full  
D. Speed: 10 Mbps, Duplex: Half  

### Answer  
The anwser is B.

### Explanation  
When **autonegotiation is disabled** on one side (SW2), the other side (SW1) can still **sense the speed**, but **cannot detect the duplex mode**.

Cisco fallback rule for **10/100 Mbps links**:

- If one side is **forced** (100/full)  
- And the other side is **auto**  
- The auto side will:  
  - Correctly detect **speed = 100 Mbps**  
  - **Default to half duplex**, because duplex cannot be negotiated

This creates a **duplex mismatch**:

- SW2 = 100 Mbps **full**  
- SW1 = 100 Mbps **half**

This leads to:

- Collisions  
- Late collisions  
- CRC errors  
- Terrible performance  

Therefore, the correct answer is **B**.

