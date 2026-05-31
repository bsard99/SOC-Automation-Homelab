# SOC-Automation-Homelab


## Overview
Built a cloud-hosted, automated incident response environment designed to ingest endpoint telemetry, trigger high-fidelity alerts for credential dumping, orchestrate threat intelligence enrichment via VirusTotal, auto-generate tickets in a case management platform, and alert analysts instantly via email.


## Architectural Diagram & Workflow
```mermaid
graph TD
    %% Define Styles
    classDef endpoint fill:#1b2a4a,stroke:#00a8cc,stroke-width:2px,color:#fff;
    classDef siem fill:#0c7b93,stroke:#00a8cc,stroke-width:2px,color:#fff;
    classDef soar fill:#27496d,stroke:#00a8cc,stroke-width:2px,color:#fff;
    classDef tool fill:#142834,stroke:#4b6584,stroke-width:1px,color:#d1d8e0;

    %% Nodes
    Win[Windows 11 Target]:::endpoint
    WazAgent[Wazuh Agent]:::endpoint
    WazMgr[Wazuh Manager Server]:::siem
    Shuffle[Shuffle SOAR Platform]:::soar
    VT[VirusTotal API<br><i>Hash Enrichment</i>]:::tool
    TheHive[TheHive Server<br><i>Auto-Case Creation</i>]:::tool
    Email[Analyst Email<br><i>Immediate Notification</i>]:::tool

    %% Connections
    Win -->|Sysmon Logs| WazAgent
    WazAgent -->|Secure Tunnel| WazMgr
    WazMgr -->|Webhook Alert JSON| Shuffle
    
    Shuffle -->|1. API Check| VT
    Shuffle -->|2. API Poster| TheHive
    Shuffle -->|3. SMTP Relay| Email
```

## Demo
[Watch the SOC Automation Demo](https://www.youtube.com/watch?v=41O4c81t-5U)

