# Quiz: Interfaces and Cables
## Quiz 1
You connect two old routers together with a UTP cable, however data is not succesfully sent and received between them. What could be the problem?

A) They are connected with a straigth-through cable
B) They are connected with a crossover cable
C) They are operating in Auto MDI-X mode

### Anwser
The correct answer is **A**

### Explanation
If operating in auto MDI-X mode, it will swap RX & TX pins automatically based on the other device. If both having this mode, the cable setup does not matter.

If it operates in crossover mode and both are not configured in auto MDI-X mode, this should work as well. The flow would be:
- TX (pin 1) from Router 1 goes to RX (pin 3) from Router 2
- TX (pin 2) from Router 1 goes to RX (pin 6) from Router 2

If it operates in straight-through mode and both are not configured in auto MDI-X mode, this will not work. The flow would be:
- TX (pin 1) from Router 1 goes to TX (pin 1) from Router 2
- TX (pin 2) from Router 1 goes to TX (pin 2) from Router 2

TX is connected to TX, and RX to RX, so no communication is possible.

---
## Quiz 2
Your company wants to connect switches in two separate buildings that are about 150m apart. They want to keep costs down, if possible. What kind of cable should they use?
A) UTP
B) Single mode fiber optic
C) Multimode fiber optic

### Anwser
The correct answer is **C**

### Explanation
UTP (copper) cables have a maximum distance of **100 meters**, so they cannot be used to connect two buildings that are 150 meters apart.

Single-mode fiber optic cables support **very long distances** (tens of kilometers) and are typically used for WAN links or connections between cities. However, they are **more expensive** and unnecessary for a 150m link.

Multimode fiber optic cables are designed for **shorter distances** (up to 550m depending on the type) and are **more cost‑effective** than single-mode fiber.  
For a 150m building-to-building connection, multimode fiber is the **cheapest and most appropriate** choice.

---
## Quiz 3
Your company wants to connect two offices that are about 3km apart. They want to keep costs down, if possible. What kind of cable should they use?

A) UTP
B) Single mode fiber optic
C) Multimode fiber optic

### Anwser
The correct answer is **B**

### Explanation
UTP (copper) cables have a maximum distance of **100 meters**, so they cannot be used to connect two offices that are 3 kilometers apart.

Multimode fiber optic cables support **shorter distances** (typically up to 550 meters depending on the type), so they are **not suitable** for a 3 km link.

Single-mode fiber optic cables are designed for **long-distance communication**, supporting several kilometers to tens of kilometers.  
Although single-mode is more expensive than multimode, it is the **only option** that can reliably cover a 3 km distance.

---
## Quiz 4
A switch has the following indication over its network interfaces:
"10/100/1000Base-T ports (1 - 24) - Ports are Auto-MDIX"
What would happen if you connect it to an identical switch using a straight-through UTP cable?

A) They would operate normally
B) They would operate at a reduced speed
C) They would not be able to communicate

### Anwser
The correct answer is **A**

### Explanation
Because the switch ports support **Auto‑MDIX**, they can automatically detect whether the connected device is the same type (switch ↔ switch) or a different type (PC ↔ switch).  
Auto‑MDIX will then **swap the TX and RX pairs internally** if needed.

This means:
- A straight‑through cable will work  
- A crossover cable will also work  
- The switch will always configure itself correctly  

Therefore, two identical switches connected with a straight‑through UTP cable will **operate normally**.

---
## Quiz 5
Your company needs to connect many end hosts to a switch which is in a wiring cabinet on the same office floor as the hosts. What kind of cable should they use?

A) UTP
B) Single mode fiber optic
C) Multimode fiber optic

### Anwser
The correct answer is **A**

### Explanation
For connecting end hosts on the same office floor, UTP (copper) cables are the standard and most cost‑effective option. UTP supports distances up to 100 meters, which is more than enough for typical same‑floor installations.

Fiber optic cables (single‑mode or multimode) are more expensive and are generally used for long‑distance links or switch‑to‑switch uplinks, not for connecting end hosts.

If it was mutliple floors or longer distances, then fiber optic would be considered, but for same floor connections, UTP is the best choice.