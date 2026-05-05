### **Current Architecture (Completed Work Only)**

### **Current Architecture (Completed Work Only)**

- Built a virtualised lab environment in VirtualBox using **two networks**:
  - **CyberLab NAT Network (192.168.100.0/24)**  
    - Provides internet access for downloading packages/updates  
    - Used by Windows Server and Wazuh Server for outbound connectivity  
  - **Host‑Only Network (192.168.56.0/24)**  
    - Used for accessing the Wazuh dashboard from the host machine  
    - Isolated from the NAT network

- Deployed **Windows Server Core**:
  - Assigned to the **CyberLab NAT network**
  - Installed **Sysmon** with SwiftOnSecurity configuration
  - Enabled **Advanced Audit Policy** using `auditpol`:
    - Logon/Logoff  
    - Account Logon  
    - Account Management  
    - Detailed Tracking (Process Creation)  
    - Other Account Logon Events  
  - Verified audit policy using `auditpol /get /category:*`
  - Verified logs using:
    - `Get-WinEvent -LogName Security`
    - `Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational"`

- Generated test events to confirm logging:
  - Logon/logoff  
  - Process execution (`whoami`, `notepad.exe`)  
  - Account creation/deletion (`net user`)  
  - Confirmed expected Security and Sysmon events appeared

- Deployed **Wazuh Server**:
  - NIC1 on **CyberLab NAT network**  
  - NIC2 on **Host‑Only network (192.168.56.x)**  
  - Confirmed dashboard accessible from host machine

- Confirmed network connectivity:
  - Windows Server → Wazuh Server (via NAT network)
  - Host machine → Wazuh dashboard (via host‑only network)




