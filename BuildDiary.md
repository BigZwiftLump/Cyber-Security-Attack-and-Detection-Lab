# Build Diary

## Day 0

- Checked hardware compatibility on home machine  
- Downloaded and installed VirtualBox  
- Installed with default settings  
- Verified that it launched correctly  

---

## Day 1

- Created a new NAT Network called **"CyberLab"** in VirtualBox  
- Set network CIDR  
- Enabled DHCP, but the plan is to assign static IPs to each VM  

---

## Day 2

- Created first VM and attached it to the NAT Network  
- Installed Ubuntu 22.04 LTS from the command line  
- Set static IP  
- Updated Ubuntu to the latest version from the command line  
- Installed **curl** (command-line tool for data transfer between a system and server using different network protocols)  
- Installed **Wazuh** (eventually) — some issues pointing to and downloading from the server, which were caused by the VM DNS  
- Checked that Wazuh installed by accessing it from a different VM using the IP address  

---

## Day 3

- Researching how to configure the lab with pfSense acting as a firewall between a virtual **external WAN** and **internal LAN**  
- The Kali attack machine to sit in the virtual WAN, with the Windows Server and Wazuh on the LAN, providing some network segmentation  

### Network Flow (Current Plan)

Kali (192.168.100.50)
        ↓
pfSense WAN (192.168.100.1)
        ↓
pfSense LAN (10.0.0.1)
        ↓
Windows Server (10.0.0.20)


- Finalised the dual‑NIC Wazuh design, confirming NIC1 on the LAN for log ingestion and NIC2 on a Host‑Only network for safe management access.
- Reworked the ASCII network diagram, correcting alignment, removing duplicate Wazuh boxes, and clearly showing the dual‑NIC architecture.
- Validated the security model, confirming that Host‑Only networking keeps the lab isolated and does not expose the real machine or home LAN.

---

## Day 4

- Tweaked the git README file to reflect the changes made to the lab architecture

