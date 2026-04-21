# Quiz: OSI model vs TCP/IP model
## Quiz 1
HTTP data sent from a YT web server is displayed via your web browser. This is an example of what?

A) Adjacent-layer interaction
B) Same-layer interaction
C) Encapsulation
D) De-encapsulation

### Anwser
The correct answer is **B**

### Explanation
This scenario describes same‑layer interaction, because the HTTP data created by the Application Layer on the YouTube web server is being interpreted by the Application Layer of your web browser. In same‑layer interaction, the same OSI layer on two different devices communicates using its own protocol — in this case, HTTP at Layer 7.

---
# Quiz 2
HTTP data has been encapsulated with three separate headers and one trailer. 
What is the appropriate name for this PDU?

A) Packet
B) Segment
C) Frame
D) Data

## Anwser
The correct answer is **C**

## Explaination
A frame is the Protocol Data Unit (PDU) used at Layer 2 (Data Link Layer).
If HTTP data has been encapsulated with three headers and one trailer, it means the data has already passed through Layers 7, 6, 5, 4, and 3 — and is now wrapped in a Layer 2 header + trailer, which forms a frame.

A trailer (specifically the FCS) only appears at Layer 2, so the correct PDU name is Frame.

---
# Quiz 3
Which layer of the OSI model are most relevant to the role of a network engineer?

A) Transport - Network - Data Link - Physical
B) Transport - Network - Data Link
C) Network only
D) Application - Presentation - Session

## Anwser
The correct answer is **A**

## Explaination
  
Network engineers primarily work with the layers responsible for moving data across networks, which are the Transport (4), Network (3), Data Link (2), and Physical (1) layers. These layers handle segmentation, routing, switching, MAC addressing, cabling, signaling, and all mechanisms required to deliver data from one device to another. The upper layers (Application, Presentation, Session) focus on software‑level functions and are mostly relevant to developers rather than network engineers, making option A the correct choice.

---
# Quiz 4
The link layer of the TCP/IP Model is equivalent to what layer, or layers, of the OSI model?

A) Transport - Network
B) Network - Data Link
C) Data Link
D) Data Link - Physical

## Anwser 
The correct answer is **D**

## Explaination
The Link Layer of the TCP/IP model combines everything that the OSI Data Link (Layer 2) and Physical (Layer 1) layers do. In the TCP/IP model, these two OSI layers are merged into a single layer responsible for framing, MAC addressing, error detection, and the actual transmission of bits over the medium. Because the TCP/IP Link Layer covers both the logical (Layer 2) and physical (Layer 1) functions, the correct match is Data Link + Physical.

---
# Quiz 5
Which layer of the OSI model provides host-to-host communications?

A) Application
B) Network
C) Transport 
D) Data Link

## Anwser
The correct answer is **C**

## Explaination
Host‑to‑host communication is provided by the Transport Layer (Layer 4). This layer creates the logical end‑to‑end connection between two hosts, manages segmentation and reassembly, handles reliability (TCP) or speed‑focused delivery (UDP), and uses port numbers to ensure data reaches the correct application. 