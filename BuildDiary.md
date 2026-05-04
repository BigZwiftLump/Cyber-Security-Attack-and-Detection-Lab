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

---

## Day 5

- Installed Windows Server 2022 on a new VirtualBox VM and assigned a static IP on the CyberLab NAT network
- Installed the Active Directory Domain Services (AD DS) role using PowerShell
- Promoted the server to a new forest (corp.local) after resolving a DSRM password complexity issue
- Rebooted into the new domain and confirmed successful promotion by logging in as CORP\Administrator

---

## Day 6

- Continued the configuration work on Windows server
	- Fixed DNS forwarder timeouts by correcting VirtualBox NAT Network attachment
	- Disabled IPv6 routing to prevent dual‑gateway conflicts
	- Verified outbound connectivity (ping 8.8.8.8, ping 1.1.1.1)
	- Confirmed DNS forwarders working via nslookup microsoft.com
	- Domain Controller now fully operational and internet‑aware
- Spent ages trying to get copy and past working between host and VM machine. Settings in VirtualBox didn't resolve it.
- Created a clean OU structure in Active Directory (allows us to create a structure that supports "least privilege" AD)
			CORP
			 ├── Admins
			 ├── Users
			 │     ├── IT
			 │     ├── Finance
			 │     ├── HR
			 │     ├── Sales
			 │     └── Operations
			 ├── Groups
			 │     ├── IT
			 │     ├── Finance
			 │     ├── HR
			 │     ├── Sales
			 │     └── Operations
			 ├── Servers
			 ├── Workstations
			 └── Service Accounts


- Created my first domain admin account (mwood.admin) and logged in with it
- Prepared baseline Group Policy structure for workstations, servers, and domain‑wide security settings
- Confirmed the DC is reachable on the network and ready for client domain joins
- Took a VirtualBox snapshot (“DC – Fresh Build + Baseline”) to preserve this clean state before expanding the lab
- Downloaded and installed Sysmon via command line and applied the sysmonconfig config settings from a xml file (from SwiftOnSecurity Github)
- Activated Module and Script Block Logging (Id 4103 and 4104 respectively)
- Tested to ensure that events were being captured under both Id's 



