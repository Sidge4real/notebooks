# Interfaces and Cables
Copyright © Lukas Van der Spiegel (author)

Focus on the trajectory for software engineering.  
These notes are written at **professional bachelor level** in applied computer science.  
They intentionally avoid deep CCNA‑exam knowledge.

---

## Interfaces
An interface is like a door on a device where the network cable plugs in.
It’s the place where a device talks to the network.

## Cables
A cable is what connects two devices so they can talk to each other.
Think of it like a wire that carries messages.

Cables can be made out of copper (twisted pair cables such as UTP/STP) or fiber optic.

### UTP Cables
UTP = Unshielded Twisted Pair

- **Unshielded**: no shielding to protect against electromagnetic interference (EMI)
- **Twisted Pair**: pairs of wires twisted together to reduce crosstalk and EMI
- Commonly used for Ethernet connections in LANs

> Includes 8 pins on the connector, which are used to transmit and receive data.

> UTP is **Full-Duplex**, meaning can transmit and receive at the same time.
Opposite is **Half-Duplex**, which is only receive or transmit at the same time.

Tx = Transmit
Rx = Receive

#### Transmit and Receive
**Router** , **Firewall** , **PC**
- Tx: 1 and 2
- Rx: 3 and 6

**Switch**
- Tx: 3 and 6
- Rx 1 and 2

#### Straight-trough Cable
When device 1:
Transmit on pins 1 and 2.
Receive on pins 3 and 6.

When device 2:
Receive on pins 1 and 2.
Transmit on pins 3 and 6.

#### Crossover Cable
When device 1:
Transmit on pins 1 and 2.
Receive on pins 3 and 6.

When device 2:
Transmit on pins 1 and 2.
Receive on pins 3 and 6.

#### Auto MDI-X
Auto MDI-X (Automatic Medium-Dependent Interface Crossover) is a feature found in modern network devices (switches, routers, PCs) that automatically swaps the transmit (Tx) and receive (Rx) pins when needed.

### Fiber Optic Cables
Fiber optic cables are used to send data using light instead of electrical signals.
They contain extremely thin strands of glass or plastic that guide light from one device to another.
Because light travels very fast and is not affected by electrical interference, fiber is ideal for high‑speed and long‑distance communication.

Fiber is commonly used in:
- Internet backbone connections
- Data centers
- Long-distance links between buildings or cities
- High-performance enterprise networks

A laser or LED sends these pulses into the fiber:
Light ON = 1
Light OFF = 0

The light stays inside the fiber because it reflects off the inner walls — a principle called total internal reflection.
This allows the signal to travel long distances with very little loss.

#### Single-mode Fiber
Allows longer cables than both UTP and multimode fiber (up to 40 km for 10 Gbps)

#### Multi-mode Fiber
Allows longer cables than UTP, but shorter cables than single-mode fiber (up to 550 meters for 10 Gbps)

### UTP vs Fiber-Optic Cables
| Feature | UTP Cable | Fiber‑Optic Cable |
| --- | --- | --- |
| **Cost** | Lower cost | Higher cost |
| **Maximum Distance** | Up to 100 meters | Up to ~40 km (single‑mode) |
| **EMI / Crosstalk** | Vulnerable to interference | Immune to interference |
| **Ports** | RJ45 ports (cheap) | SFP ports (more expensive) |
| **Security** | Emits small electrical signals → can be copied | No signal leakage → very secure |
| **Speed** | Good for typical LAN speeds | Excellent for high‑speed, long‑distance links |