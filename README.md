# Task 4 - Setup and Use a Firewall (Linux)

## Objective
To configure and test basic firewall rules using UFW (Uncomplicated Firewall) on Linux.
The goal of this task is to learn how to allow and block specific ports, verify firewall status, test connections, and understand how network traffic filtering improves system security.

---

## Tools Used
- Ubuntu Linux
- UFW (Uncomplicated Firewall)
- Netcat (nc) - for testing open and blocked ports

---

## Steps Performed

### Step 1: Install and Enable UFW
```bash
sudo apt install ufw -y
sudo ufw enable
sudo ufw status
```
Checked that the firewall was installed and active.

---

### Step 2: Allow SSH (Port 22)
```bash
sudo ufw allow 22/tcp
```
SSH was allowed to keep secure remote access available.

---

### Step 3: Block Telnet (Port 23)
```bash
sudo ufw deny 23/tcp
```
Telnet is insecure because it transmits data in plain text. Blocking it helps prevent attacks.

---

### Step 4: Verify Firewall Rules
```bash
sudo ufw status numbered
```
Verified that SSH (port 22) was allowed and Telnet (port 23) was denied.

---

### Step 5: Test Firewall Rules
Used netcat (nc) to check the allowed and blocked ports.
```bash
nc -zv localhost 22   # Connection succeeded
nc -zv localhost 23   # Connection refused or timed out
```
Port 22 (SSH) responded successfully.  
Port 23 (Telnet) was blocked, showing "Connection refused."

---

### Step 6: Delete the Test Rule and Restore State
```bash
sudo ufw delete 2
sudo ufw disable
```
Removed the test rule and disabled UFW to restore the original system state.

---

## Summary of Work Done
| Step | Action | Result |
|------|--------|--------|
| 1 | Installed & enabled UFW | Firewall active |
| 2 | Allowed SSH (port 22) | Secure access allowed |
| 3 | Denied Telnet (port 23) | Insecure access blocked |
| 4 | Verified rules | Correct configuration confirmed |
| 5 | Tested ports | SSH open, Telnet blocked |
| 6 | Deleted rule & disabled firewall | Restored default state |

---

## Outcome
- Gained practical experience in configuring UFW firewall on Linux.
- Understood how to allow and block ports for network security.
- Verified firewall operation using real-time connection testing.
- Learned how to safely enable, test, and disable a firewall.

---

## Key Concepts Learned
- Firewall: A network security system that filters traffic.
- UFW: A simple tool for managing firewall rules on Ubuntu.
- Allow/Deny Rules: Used to control inbound or outbound traffic.
- Ports: Network endpoints for different services (e.g., 22 for SSH, 23 for Telnet).
- Traffic Filtering: Blocking unnecessary or unsafe connections to protect systems.

---

## Interview Questions and Answers

### 1. What is a firewall?
A firewall is a security system that monitors and controls incoming and outgoing network traffic based on security rules.
It acts as a barrier between a trusted internal network and untrusted external networks (like the internet).

---

### 2. Difference between stateful and stateless firewalls?
| Type | Description | Example |
|------|--------------|----------|
| Stateless Firewall | Inspects each packet independently, without remembering previous packets. | Basic packet filter |
| Stateful Firewall | Tracks the state of connections and allows only packets related to valid sessions. | UFW, Windows Firewall |

Example: A stateful firewall knows which responses belong to a valid request, while a stateless one doesn't.

---

### 3. What are inbound and outbound rules?
- Inbound Rules: Control traffic coming into your system.  
  Example: Allow SSH on port 22.
- Outbound Rules: Control traffic leaving your system.  
  Example: Restrict apps from sending data externally.

---

### 4. How does UFW simplify firewall management?
UFW (Uncomplicated Firewall) provides a simple way to manage complex iptables rules.
Instead of writing long and confusing commands, you can use:
```bash
sudo ufw allow 22/tcp
sudo ufw deny 23/tcp
```
Easy, quick, and beginner-friendly.

---

### 5. Why block port 23 (Telnet)?
Telnet uses port 23 and sends all data in plain text, including usernames and passwords.
It's unsafe and can be exploited by hackers using sniffing tools.
Modern systems use SSH (port 22) instead, which encrypts all communication.

---

### 6. What are common firewall mistakes?
- Forgetting to allow SSH before enabling the firewall.
- Keeping unnecessary ports open.
- Creating conflicting rules.
- Deleting the wrong rule without checking its number.
- Not saving or checking the status after configuration.

---

### 7. How does a firewall improve network security?
- Blocks unauthorized access and potential attacks.
- Prevents data leakage by controlling outbound connections.
- Reduces malware infection spread.
- Acts as the first defense layer for systems and networks.

---

### 8. What is NAT in firewalls?
NAT (Network Address Translation) allows multiple devices on a local network to share a single public IP address.
It hides private IPs from external access, improving security and saving IP space.

Example: Your Wi-Fi router uses NAT to connect all your home devices to the internet using one public IP.

---

## Summary Table
| Concept | Explanation |
|----------|--------------|
| Firewall | Filters network traffic |
| Stateful | Tracks ongoing sessions |
| Stateless | Checks individual packets |
| UFW | Simplifies iptables configuration |
| Port 22 | SSH - allowed |
| Port 23 | Telnet - blocked |
| NAT | Hides private IPs behind public IP |
| Inbound | Controls incoming traffic |
| Outbound | Controls outgoing traffic |

---

## Repository Includes
- Screenshot evidence of UFW configuration and testing.
- This detailed README.md file explaining setup, verification, and Q&A.
- Command log and notes from Linux terminal.

---

## Author
- Name: Aashish
- Program: Cyber Security Internship
- Date: 29 October 2025
- Task: 4 - Setup and Use a Firewall (Linux)

---
