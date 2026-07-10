# Network Penetration Testing Report

**Project:** CloudExify Summer Internship 2026 - Month 1 Project 1  
**Intern Name:** Muhammad Subhan  
**Target IP:** `10.0.2.4`  
**Attacker IP:** `10.0.2.3`  

---

### 1. Executive Summary
An authorized network penetration test was conducted on the isolated target host `10.0.2.4` to identify open ports, active services, and potential security vulnerabilities.

### 2. Methodology
The assessment followed standard penetration testing steps:
* **Reconnaissance:** Verified host availability using ICMP Ping.
* **Scanning & Enumeration:** Executed an aggressive service version scan using Nmap[cite: 1].
* **Traffic Analysis:** Monitored network interactions via Wireshark[cite: 1].

### 3. Key Findings
* **Host OS:** Unix (Samba 3.0.20-Debian)
* **Critical Vulnerability:** 
- The target host (10.0.2.4) has multiple open ports including FTP (21), SSH (22), Telnet (23), HTTP (80), SMB (139,445), MySQL (3306), PostgreSQL (5432), and Apache Tomcat (8180).
- Anonymous FTP login is enabled.
- SMB message signing is disabled, increasing the risk of Man-in-the-Middle (MITM) attacks.
- Telnet and FTP transmit data in plain text, making credentials vulnerable to interception.
- The system is running outdated software versions that may contain known vulnerabilities.
* **Unencrypted Protocols:** Cleartext protocols (like FTP/Telnet) are available on the target, risking credential exposure[cite: 1].

* ## 4. Wireshark Traffic Analysis

Wireshark was used to monitor network traffic during the assessment.

Observed protocols:
- NTP (Network Time Protocol)
- ARP (Address Resolution Protocol)

Observations:
- NTP traffic was exchanged between 10.0.2.3 and 203.80.128.20.
- ARP requests and replies were observed between the attacker and gateway.
- No encrypted application traffic was observed during the capture.

### 5. Remediation & Recommendations
- Disable Anonymous FTP access.
- Disable Telnet and use SSH instead.
- Enable SMB message signing.
- Update outdated services and operating system packages.
- Restrict unnecessary open ports using a firewall.
- Perform regular vulnerability assessments.


## 6. Conclusion

The penetration test successfully identified multiple exposed services and insecure configurations on the target system. Implementing the recommended security controls will significantly reduce the attack surface and improve the overall security posture.
