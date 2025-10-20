# SMB File Access Investigation

## Overview

Traced internal file access patterns to identify the origin point of a sensitive document before external exfiltration. Demonstrated ability to track lateral movement and file access within enterprise networks using SMB protocol analysis.

## Scenario

File "Super_important_file_of_secrets.docx" was discovered on an external FTP server. Investigation required identifying which internal protocol was used to access this file within the CORP network before exfiltration occurred.

## Tools Used

- **Elastic SIEM** - Log analysis and dashboard visualization
- **Zeek** - Network protocol monitoring and file tracking
- **Query Language** - KQL for targeted file investigation

## Investigation Process

### 1. File Identification
- Searched Zeek-FILES Dashboard for target file
- Query: `file.name : "Super_important_file_of_secrets.docx"`
- Analyzed Top Application Protocols panel

### 2. Protocol Analysis
- Identified SMB (Server Message Block) as the internal access protocol
- Confirmed file was accessed via SMB before FTP exfiltration
- Traced internal file movement within CORP network

### 3. Key Findings
- **Protocol Used:** SMB (port 445)
- **Access Location:** Internal CORP network
- **Significance:** Indicates lateral movement before exfiltration
- **Attack Chain:** Internal SMB access → External FTP transfer

## MITRE ATT&CK Mapping

- **T1021.002** - Remote Services: SMB/Windows Admin Shares
- **T1570** - Lateral Tool Transfer
- **T1083** - File and Directory Discovery

## Skills Demonstrated

- SMB protocol analysis and file tracking
- Elastic SIEM dashboard navigation and filtering
- Multi-stage attack investigation (internal access → external exfiltration)
- Understanding enterprise file-sharing protocols
- KQL query development for file forensics

## Conclusions

Successfully identified SMB as the internal protocol used to access the sensitive file before exfiltration. This investigation demonstrates understanding of lateral movement techniques and the ability to trace file access across multiple attack stages within enterprise environments.

---

**Portfolio:** [github.com/paigealfred](https://github.com/paigealfred)
