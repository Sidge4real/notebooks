# Quiz: Dynamic Routing
## Quiz 1
R1 learns four routes to 192.168.1.0/24 through multiple routing protocols: RIP, EIGRP, OSPF and IS-IS. Which route/routes will be added to the route table?

A) RIP route only
B) EIGRP route only
C) OSPF route only
D) IS-IS route only
E) RIP and EIGRP routes, because both are distance vector protocols.
F) OSPF and IS-IS routes, because both are link state protocols.
G) All four routes will be added.

### Anwser
Anwser is B.

### Explanation
Routers choose the route with the **lowest Administrative Distance (AD)** when multiple protocols advertise the same destination.

AD values:  
- EIGRP → **90**  
- OSPF → 110  
- IS‑IS → 115  
- RIP → 120  

The lowest AD wins → **EIGRP (90)**.  
Therefore, only the **EIGRP route** is installed in the routing table.

---

## Quiz 2
Which type of routing protocol is also known as "routing by rumor"?

A) Link state protocols
B) Path Vector protocols
C) Distance Vector protocols
D) Interior Gateway protocols

### Anwser
Anwser is C.

### Explanation
Distance Vector protocols (like RIP) are called **“routing by rumor”** because routers do **not** know the full network topology.  
They only know what their **neighbors tell them**, and they pass that information along.  
This can lead to slow convergence and routing loops, which is why techniques like split horizon and poison reverse exist.

---

## Quiz 3
R1 learns 2 routes to 172.16.0.0/16 via RIP, one via 10.0.0.1 and the other via 10.1.0.1
Both routes are 5 hops away. Which route/routes will be entered into the routing table?

A) Both routes
B) Only the route via 10.0.0.1
C) Only the route via 10.1.0.1
D) Neither route will be added because RIP's AD value is too high.

### Anwser
Anwser is A.

### Explanation
RIP supports **equal‑cost load balancing**.  
If two routes have:
- the **same prefix**,  
- the **same metric** (hop count),  
- and come from the **same protocol**,  

then **both** are installed in the routing table.

Since both RIP routes have a hop count of **5**, R1 installs **both** and load‑balances traffic across them.

---

## Quiz 4
RouterA has the following routes in its routing table:

S 10.20.0.0/22 [1/0] via 192.168.10.2  
D 10.20.0.0/24 [120/3] via 192.168.10.3  
D 10.20.0.0/26 [90/28089656] via 192.168.10.4  
D 10.20.0.0/28 [110/64] via 192.168.10.1  

RouterA receives a packet destined for **10.20.0.14**.  
Which route will RouterA use?

A) the RIP route, because it has the highest administrative distance  
B) the OSPF route, because it is the route with the longest prefix match  
C) the static route, because static routes are preferred over dynamic routes  
D) the EIGRP route, because it has the lowest administrative distance  

### Answer
Anwser is B.

### Explanation
Routers always follow this decision order:

1. **Longest prefix match**  
2. If multiple routes match equally → choose **lowest AD**  
3. If AD is equal → choose **lowest metric**

Step 1 decides everything here.

Check which prefix includes **10.20.0.14**:

- 10.20.0.0/22 → covers .0 to .3 (matches)  
- 10.20.0.0/24 → covers .0 to .255 (matches)  
- 10.20.0.0/26 → covers .0 to .63 (matches)  
- 10.20.0.0/28 → covers .0 to .15 (**matches and is the most specific**)  

The **/28** route is the longest prefix match.  
Even though its AD (110, OSPF) is not the lowest, **prefix length always wins first**.

Therefore, RouterA uses the **OSPF /28 route**.

