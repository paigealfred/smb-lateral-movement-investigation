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

# SMB File Access Investigation

## Overview

Traced internal file access patterns to identify the origin point of a sensitive document before external exfiltration. Demonstrated ability to track lateral movement and file access within enterprise networks using SMB protocol analysis.

## Lab Challenge

![Investigation Question](lab-challenge-question.png)

*Challenge 4.3.9: Which application layer protocol was used internally within the CORP network to access 'Super_important_file_of_secrets.docx'?*

## Scenario

File "Super_important_file_of_secrets.docx" was discovered on an external FTP server. Investigation required identifying which internal protocol was used to access this file within the CORP network before exfiltration occurred.

## Tools Used

- **Elastic SIEM** - Log analysis and dashboard visualization
- **Zeek** - Network protocol monitoring and file tracking
- **KQL (Kibana Query Language)** - Targeted file search queries

## Investigation Process

### 1. Search Zeek-FILES Dashboard

![Zeek FILES Dashboard with Query](file-search-query.png)

*Opened Zeek-FILES-Dashboard in Elastic and executed KQL query: `file.name : "Super_important_file_of_secrets.docx"` to filter logs specifically for the target file*

### 2. Analyze Top Application Protocols

![Top Application Protocols - SMB Result](smb-protocol-confirmation.png)

*Reviewed Top Application Protocols panel which revealed SMB as the internal protocol used to access the file within the CORP network*

## Key Findings

- **Protocol Identified:** SMB (Server Message Block)
- **Port:** 445 (standard SMB port)
- **Access Location:** Internal CORP network (172.16.100.x subnet)
- **File Accessed:** Super_important_file_of_secrets.docx
- **Significance:** Internal SMB file access preceded external FTP exfiltration
- **Attack Pattern:** Internal reconnaissance via SMB → File discovery → External data theft

## MITRE ATT&CK Mapping

- **T1021.002** - Remote Services: SMB/Windows Admin Shares
- **T1570** - Lateral Tool Transfer  
- **T1083** - File and Directory Discovery
- **T1039** - Data from Network Shared Drive

## Skills Demonstrated

- **Elastic SIEM Navigation** - Dashboard usage and KQL filtering
- **KQL Query Development** - Precise file tracking queries
- **SMB Protocol Analysis** - Understanding enterprise file-sharing protocols
- **File Forensics** - Tracing document access across network segments
- **Multi-Stage Investigation** - Connecting internal access to external exfiltration
- **Attack Chain Reconstruction** - Understanding lateral movement techniques

## Technical Details

**SMB (Server Message Block):**
- Application-layer protocol for file sharing over networks
- Commonly used in Windows environments for shared drives and lateral movement
- Port 445 (TCP)
- Critical protocol for detecting insider threats and lateral movement in enterprise SOCs

**Investigation Methodology:**
1. Identified target file on external FTP server (from related investigation)
2. Opened Zeek-FILES Dashboard in Elastic SIEM
3. Executed KQL query to filter for specific filename
4. Analyzed Top Application Protocols panel to determine internal access method
5. Confirmed SMB as the protocol used within CORP network
6. Correlated internal SMB access with subsequent external FTP exfiltration

## Conclusions

Successfully identified SMB as the internal protocol used to access sensitive file before exfiltration. This investigation demonstrates:

- Understanding of enterprise file-sharing protocols and their role in attacks
- Ability to track file access across network segments
- Recognition of lateral movement and reconnaissance indicators
- Skill in correlating internal activity with external data theft
- Proficiency with Elastic SIEM, Zeek, and KQL for file forensics

**Complete Attack Chain:** Internal SMB Access → File Discovery → External FTP Exfiltration

## Related Investigations

This project directly connects with my [FTP Data Exfiltration Investigation](https://github.com/paigealfred/ftp-exfiltration-investigation) where the same file was transferred externally via FTP to 85.93.20.10 after initial SMB access on the internal network.

---

**Portfolio:** [github.com/paigealfred](https://github.com/paigealfred)
