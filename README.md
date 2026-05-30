# SOC-Automation-Homelab


## Overview
Built a cloud-hosted, automated incident response environment designed to ingest endpoint telemetry, trigger high-fidelity alerts for credential dumping, orchestrate threat intelligence enrichment via VirusTotal, auto-generate tickets in a case management platform, and alert analysts instantly via email.


## Architectural Diagram & Workflow
[Windows 11 Target] ──(Sysmon logs)──> [Wazuh Agent]
                                            │
                                    (Secure Tunnel)
                                            ▼
[Shuffle SOAR] <──(Webhook Alert)─── [Wazuh Manager Server]
      │
      ├─(API Check)───> [VirusTotal API] (Hash Enrichment)
      ├─(API Poster)──> [TheHive Server]  (Auto-Case Creation)
      └─(SMTP Relay)──> [Analyst Email]   (Immediate Notification)
