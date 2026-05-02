```mermaid

    %% WAN Side
    subgraph WAN["CyberLab NAT Network (WAN)"]
        KALI["Kali<br>192.168.100.50"]
        PFWAN["pfSense WAN<br>192.168.100.1"]
    end

    %% LAN Side
    subgraph LAN["Internal Network (LAN)"]
        PFLAN["pfSense LAN<br>10.0.0.1"]
        WIN["Windows Server<br>10.0.0.20<br>Wazuh Agent Installed"]
        WAZUH["Wazuh Server (SIEM)<br>10.0.0.10"]
    end

    %% Traffic Flow
    KALI -->|Attacks| PFWAN
    PFWAN --> PFLAN
    PFLAN --> WIN

    %% Alerting Flow
    WIN -->|Logs & Alerts| WAZUH
    PFLAN -->|Firewall Alerts| WAZUH
