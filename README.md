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
* **Critical Vulnerability:** SMBv1 Message Signing is **Disabled (Dangerous)**. This misconfiguration allows attackers to perform Man-in-the-Middle (MITM) attacks and hijack sessions.
* **Unencrypted Protocols:** Cleartext protocols (like FTP/Telnet) are available on the target, risking credential exposure[cite: 1].

### 4. Remediation & Recommendations
* **Enforce Message Signing:** Enable SMB signing by updating `smb.conf` with `server signing = mandatory`.
* **Disable Insecure Services:** Turn off legacy or unencrypted protocols and enforce secure alternatives like SSH (Port 22)[cite: 1].
