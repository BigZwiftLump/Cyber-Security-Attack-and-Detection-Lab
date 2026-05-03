# 🔐 Cybersecurity Attack & Detection Lab

I’ve built a self‑contained, isolated security lab designed to simulate real‑world adversary behaviour, endpoint telemetry, and SIEM‑driven detection workflows.  
This environment supports and demonstrates hands‑on learning, threat‑hunting practice, and blue‑team analysis.

---

## 🧩 Lab Architecture

My lab runs across **three isolated VirtualBox networks**, routed and filtered through pfSense.

### **1. CyberLab NAT Network (WAN) — 192.168.100.0/24**
Used for attacker traffic and pfSense WAN‑side logging.

| Component | IP | Role |
|----------|----|------|
| **Kali Linux (Attacker)** | `192.168.100.50` | Executes offensive techniques |
| **pfSense (WAN Interface)** | `192.168.100.1` | Firewall - Receives and logs inbound attack traffic |

---

### **2. Internal Network (LAN) — 10.0.0.0/24**
My protected internal segment behind pfSense.

| Component | IP | Role |
|----------|----|------|
| **pfSense (LAN Interface)** | `10.0.0.1` | Firewall - Routes and filters internal traffic |
| **Windows Server (Target)** | `10.0.0.20` | Generates Sysmon, PowerShell & Security logs |
| **Wazuh Server (NIC1)** | `10.0.0.10` | Receives logs from Windows Server and pfSense Firewalls |

---

### **3. Host‑Only Management Network — 192.168.56.0/24**
Used for safe access to the SIEM dashboard from my host machine.

| Component | IP | Role |
|----------|----|------|
| **Host Machine** | `192.168.56.1` | Accesses Wazuh dashboard |
| **Wazuh Server (NIC2)** | `192.168.56.x` | Exposes SIEM UI to host‑only network |

---

## 🔄 Data Flow

1. I launch attacks from **Kali Linux** into the CyberLab NAT network  
2. Traffic hits **pfSense**, which generates logs and forwards traffic into the internal LAN  
3. **Windows Server** generates security logs (Sysmon, PowerShell, Security)  
4. The **Wazuh Agent** forwards logs to the Wazuh SIEM  
5. **Wazuh** correlates events, applies detection rules, and raises alerts  
6. I investigate alerts via the Wazuh Dashboard over the Host‑Only network  

---

## 🎯 Purpose

This lab helps me develop skills in:

- Threat detection engineering  
- Incident response  
- Log analysis & correlation  
- Adversary emulation  
- Blue‑team investigation  
- Hands‑on SIEM/EDR workflows  

---

## 🛠️ Technologies Used

- **Wazuh** (SIEM/EDR)  
- **Sysmon** (Endpoint telemetry)  
- **pfSense** (Firewall & packet logging)  
- **Kali Linux** (Offensive tooling)  
- **Windows Server** (Target host)  
- **Oracle VirtualBox** (VMs and multi‑network setup)
- **Git** (Version control for lab documentation and configuration)

---

## 📈 Planned Future Enhancements

- MITRE ATT&CK‑mapped detection rules  
- Automated attack chains (Atomic Red Team / Caldera)  
- Additional Windows endpoints  
- Elastic / HELK integration  
