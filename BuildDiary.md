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


- So today, in order to facilitate this, I will need to create a new **host-only internal network** in VirtualBox and assign my Windows Server and Wazuh Server new static IP addresses on the newly created internal LAN  

---

