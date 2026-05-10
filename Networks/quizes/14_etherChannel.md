# Quiz: EtherChannel
## Quiz 1
Which of the following **channel-group mode** combinations will result in an operational EtherChannel? (choose three)

A) on - on
B) passive - passive
C) desirable - auto
D) auto - auto
E) active - desirable
F) on - desirable
G) active - active

### Anwsers
Anwsers are A, C, G

### Explanation
#### ✔ A) on - on → Works  
This is **static EtherChannel**.  
Both sides force the channel into an EtherChannel without using any negotiation protocol.  
Because neither side expects LACP or PAgP frames, the bundle forms as long as:  
- speed/duplex match  
- trunk/access mode match  
- allowed VLANs match  
- channel-group number matches  

Static EtherChannel is simple but dangerous:  
It cannot detect mismatches, so the channel may appear “up” even if traffic fails.

#### ✔ C) desirable - auto → Works  
This is **PAgP** (Cisco proprietary).  
- `desirable` = actively sends PAgP negotiation frames  
- `auto` = listens and responds  

PAgP forms an EtherChannel when **at least one side is desirable**.  
This combination is the classic working PAgP setup.

#### ✔ G) active - active → Works  
This is **LACP** (industry standard).  
- `active` = actively sends LACP negotiation frames  
- `active` = actively sends LACP negotiation frames  

Both sides initiate negotiation, so the EtherChannel forms immediately.  
LACP is preferred in modern networks because it is open-standard and supports up to 16 interfaces (8 active, 8 standby).

#### ✘ B) passive - passive  
LACP:  
- `passive` = listens but does NOT initiate  

If both sides are passive, no LACP frames are sent.  
No negotiation = no EtherChannel.  
This is the LACP equivalent of “auto-auto” in PAgP.

#### ✘ D) auto - auto  
PAgP:  
- `auto` = listens but does NOT initiate  

Same issue as passive-passive.  
Both sides wait, nobody initiates → no EtherChannel.

#### ✘ E) active - desirable  
This is a **protocol mismatch**.  
- `active` = LACP  
- `desirable` = PAgP  

LACP and PAgP cannot communicate.  
They send different negotiation frames, so neither side recognizes the other.

#### ✘ F) on - desirable  
Another **protocol mismatch**.  
- `on` = static EtherChannel (no negotiation)  
- `desirable` = PAgP (expects negotiation)  

Static mode does not send negotiation frames.  
PAgP waits for negotiation frames that never arrive → no EtherChannel.

### Summary Table

| Combination | Protocol | Result | Reason |
|------------|----------|--------|--------|
| on - on | Static | ✔ Works | Both sides force the channel |
| desirable - auto | PAgP | ✔ Works | One side initiates |
| active - active | LACP | ✔ Works | Both sides initiate |
| passive - passive | LACP | ✘ No | No one initiates |
| auto - auto | PAgP | ✘ No | No one initiates |
| active - desirable | LACP vs PAgP | ✘ No | Protocol mismatch |
| on - desirable | Static vs PAgP | ✘ No | Protocol mismatch |

---
## Quiz 2
In the output of the `show etherchannel summary` command, you notice that the physical interfaces in the etherchannel you configured have the flag **P** nex to them. What does this mean?

A) The interfaces are in LACP Passive mode.
B) The interfaces are bundled in the port channel.
C) The interfaces are paused until the other switch's etherchannel is configured.
D) The etherchannel is layer 2 etherchannel.

### Anwser
Anwser is B.

### Explanation
The flag **P** stands for **"bundled in port-channel"**.

This means:
- The interface is **successfully participating** in the EtherChannel.
- It is **actively forwarding traffic** as part of the Port‑Channel.
- There are **no mismatches** (speed, duplex, trunking, VLANs, protocol).
- The EtherChannel negotiation (LACP/PAgP) succeeded, or static mode matched.

Other common flags for context:
- **I** = Individual (not bundled, mismatch or negotiation failed)  
- **D** = Down  
- **S** = Layer 2 EtherChannel  
- **R** = Layer 3 EtherChannel  

The **P** flag is exactly what you want to see.

---

## Quiz 3
Which of the following member interface params need to match to form an etherchannel? (choose two)

A) interface ID
B) IP address
C) interface speed
D) switchport mode (access/trunk)

### Anwsers
Anwsers are C, D

### Explanation
EtherChannel requires that **all physical interfaces in the bundle have identical Layer 1 and Layer 2 settings**.  
If they differ, the switch will place the interface in **I (Individual)** mode and refuse to bundle it.

#### ✔ C) interface speed  
All member interfaces must run at the **same speed**.  
Example:  
- 1 Gbps + 1 Gbps → OK  
- 1 Gbps + 100 Mbps → NOT OK  

If speeds differ, the hashing algorithm and load balancing cannot operate correctly.

#### ✔ D) switchport mode (access/trunk)  
All interfaces must be either:
- all **access**, or  
- all **trunk**  

If trunk:
- allowed VLANs must match  
- native VLAN must match  

If access:
- access VLAN must match  

#### ✘ A) interface ID  
The physical interface numbers do not need to match.  
Example:  
- Switch A uses g0/1 and g0/2  
- Switch B uses g0/3 and g0/4  
This is perfectly fine.

#### ✘ B) IP address  
Member interfaces **never** have IP addresses in Layer 2 EtherChannel.  
Only the **Port‑Channel interface** may have an IP (in Layer 3 EtherChannel).

---

## Quiz 4
You configure EtherChannel on two switches as follows:

**SwitchA**
- channel-protocol lacp  
- channel-group 1 mode on  

**SwitchB**
- channel-protocol pagp  
- channel-group 1 mode on  

What is the result of this configuration?

A) A link is formed using LACP because it was configured first and has priority.  
B) No link is formed.  
C) A link is formed using PAgP because it was configured last and has priority.  
D) A link is formed without an aggregation protocol.

### Answer
Anwser is B

### Explanation
Even though both switches use **mode on**, which creates a **static EtherChannel**, the configuration still fails.

Here is why:

- `channel-protocol lacp` tells SwitchA to expect **LACP** frames.  
- `channel-protocol pagp` tells SwitchB to expect **PAgP** frames.  
- But **mode on does NOT send negotiation frames** (no LACP, no PAgP).  
- Because no negotiation frames are sent, both switches rely on **static matching**.

However, the **protocol setting must still match** on both sides.  
If one side is forced to LACP and the other to PAgP, the switches treat the configuration as **incompatible**.

Result:  
The interfaces will show as **I (Individual)** in `show etherchannel summary`, meaning they do NOT bundle.

Therefore, **no EtherChannel is formed**.
