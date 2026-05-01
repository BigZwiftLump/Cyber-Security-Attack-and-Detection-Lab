# 🔐 Cybersecurity Attack & Detection Lab

A self‑contained, isolated security lab designed to simulate real‑world adversary behaviour, endpoint telemetry, and SIEM‑driven detection workflows.  
This environment supports hands‑on learning, threat‑hunting practice, and blue‑team analysis.

---

## 🧩 Lab Architecture

**Network:** Isolated NAT network — `192.168.100.0/24`

| Component | IP | Role |
|----------|----|------|
| **pfSense Firewall** | `192.168.100.1` | Network segmentation & traffic logging |
| **Wazuh Server (SIEM/EDR)** | `192.168.100.10` | Log collection, correlation, alerting |
| **Windows Server (Target)** | `192.168.100.20` | Generates Sysmon, PowerShell & Security logs |
| **Kali Linux (Attacker)** | `192.168.100.50` | Executes offensive techniques |

---

## 🔄 Data Flow

1. **Kali Linux** launches attacks against the Windows Server  
2. **Windows Server** generates security logs (Sysmon, PowerShell, Security)  
3. **Wazuh Agent** forwards logs to the Wazuh SIEM  
4. **Wazuh** correlates events, applies detection rules, and raises alerts  
5. **Analyst** investigates alerts in the Wazuh Dashboard  
6. **pfSense** logs all network traffic for additional analysis  

---

## 🎯 Purpose

This lab is built to support:

- Threat detection engineering  
- Incident response practice  
- Log analysis & correlation  
- Adversary emulation  
- Blue‑team skill development  
- Hands‑on SIEM/EDR learning  

---

## 🛠️ Technologies Used

- **Wazuh** (SIEM/EDR)  
- **Sysmon** (Endpoint telemetry)  
- **pfSense** (Firewall & packet logging)  
- **Kali Linux** (Offensive tooling)  
- **Windows Server** (Target host)  

---

## 📈 Future Enhancements

- MITRE ATT&CK‑mapped detection rules  
- Automated attack chains (Atomic Red Team / Caldera)  
- Additional Windows endpoints  
- Elastic / HELK integration  