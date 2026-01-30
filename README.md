# SOC Automation & Threat Detection Lab (Wazuh SIEM)

## Project Overview
This project demonstrates the deployment of a Security Information and Event Management (SIEM) system using Wazuh. I built a virtualized lab environment to monitor Windows endpoints, analyze security telemetry, and detect active threats such as Brute Force attacks.

## 🛠 Tools & Technologies
* SIEM: Wazuh (Manager, Indexer, Dashboard)
* Virtualization: Oracle VM VirtualBox
* Endpoint: Windowsvm 11 (Victim)
* Network: Host-Only Adapter (Private Lab Subnet)
* Security Logs: Windows Event Viewer (Event ID 4625)

## 🏗 Lab Architecture
1.  Wazuh Manager: Centralized engine for log analysis and alerting.
2.  Windows Agent: Installed on the target VM to collect and forward system logs.
3.  Network Configuration: Configured a static IP environment (`192.168.56.0/24`) to ensure stable communication between the agent and manager.

## 🛡 Incident Simulation: Brute Force Attack
To test the detection capabilities, I simulated a brute-force attack by attempting multiple failed logons on the Windows VM.

### 1. Detection
The Wazuh Analysis Engine correlated the failed attempts and triggered a **High Severity Alert (Level 10)**.

### 2. Analysis
| Field | Value |
| :--- | :--- |
| **Rule ID** | 60122 |
| **Description** | Multiple Windows logon failures |
| **Alert Level** | 10 (High Severity) |
| **Source IP** | 192.168.56.X |
| **Event ID** | 4625 (Logon Failure) |


### 3. Visualizations
<img width="1919" height="892" alt="Screenshot 2026-01-30 095947" src="https://github.com/user-attachments/assets/c023b8c1-830d-4d70-ad4f-d29f33441cd0" />
<img width="1906" height="877" alt="Screenshot 2026-01-30 100820" src="https://github.com/user-attachments/assets/22183ef1-9bd6-4220-9af1-62cbe793e2cd" />

## 🚀 Key Achievements
* Successfully installed and configured **Wazuh Manager** on a Linux VM.
* Deployed and registered **Wazuh Agents** using custom authentication keys.
* Modified `ossec.conf` to enable **File Integrity Monitoring (FIM)** and **Real-time Log Collection**.
* Verified security auditing policies via Windows `auditpol`.

## 📚 Lessons Learned
* **Network Persistence:** Learned how to troubleshoot VM connectivity issues by moving from NAT to Host-Only/Bridged adapters.
* **Log Correlation:** Understood how SIEMs use rules to turn hundreds of "Level 5" events into a single actionable "Level 10" alert.
* **Incident Lifecycle:** Followed the NIST Incident Response framework to identify, analyze, and document threats.
