# Quiz: CLI

## Quiz 1
What kind of cable is used to connect to a Cisco device via the RJ45 console port?

A) Rollover cable  
B) Crossover cable  
C) USB cable  

### Answer
The correct anwser is **A**

### Explanation
A Cisco console port uses a **rollover cable** (light‑blue console cable).  
It connects:

- RJ‑45 → Cisco console port  
- DB9 → PC (or via USB‑to‑serial adapter)

A crossover cable is used for network connections, not console access.

---

## Quiz 2
You type `enable` to enter privileged EXEC mode on your Cisco router, however the password you enter is not accepted. What could be the problem?

A) `service password-encryption` is enabled  
B) `service password-encryption` is disabled  
C) Caps Lock is on  

### Answer
The correct anwser is **C**

### Explanation
`service password-encryption` only affects how passwords are **stored** in the configuration, not how you type them.  
If the password is rejected, the most likely cause is a typing issue — often **Caps Lock**.

---

## Quiz 3
What is the most secure method to protect access to privileged EXEC mode?

A) The `enable secret` command  
B) The `enable password` command  
C) The `enable password` command, with `service password-encryption`  

### Answer
The correct anwser is **A**

### Explanation
`enable secret` uses a **strong, non‑reversible hash** (type 5 or 9).  
`enable password` uses **type 7**, which is reversible and insecure — even with `service password-encryption`.  
Therefore, `enable secret` is always the most secure option.

---

## Quiz 4
If both the `enable password` and the `enable secret` command are configured, what happens when you use `enable` to enter privileged EXEC mode?

A) You must enter the enable password, followed by the enable secret  
B) You must enter the enable password only  
C) You must enter the enable secret only  

### Answer
The correct anwser is **C**

### Explanation
When both are configured, **Cisco always prioritizes the `enable secret`**.  
The `enable password` is ignored.

---

## Quiz 5
You enter the `config t` command to enter global configuration mode. What is the full-length version of the command?

A) configuration time  
B) configure terminal  
C) configuration terminal  

### Answer
The correct anwser is **B**

### Explanation
`config t` is shorthand for: configure terminal
This command places you in **global configuration mode**, where device‑wide settings can be modified.