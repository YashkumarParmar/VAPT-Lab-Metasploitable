# VAPT-Lab-Metasploitable
## 🎯 Project Title & Brief Overview

> Set up an isolated testing network using VirtualBox containing a Kali Linux and a vulnerable Metasploitable 2 server.  
> Conducted network scans using Nmap to find open ports and ran an automated Nessus assessment to uncover 69 distinct system weaknesses.  
> Used Burp Suite to manually exploit a web command injection vulnerability and used the terminal to log into exposed Telnet and FTP services.  

---

## ⚙️ Technologies & Tools Used

| Component | Description |
|------------|-------------|
| **Virtualization** | Oracle VirtualBox |
| **Operating Systems** | Kali Linux (Attacker Platform), Metasploitable 2 (Legacy Target Host) |
| **Network & Traffic Analysis** | Nmap, Wireshark |
| **Vulnerability Management** | Tenable Nessus Essentials, Nikto |
| **Web Application Interception** | Burp Suite (Community Edition) |
| **Protocols Audited** | TCP, HTTP, FTP, Telnet, VNC |

---

## 🌐 Lab Environment / Architecture

<img width="1408" height="768" alt="Diagram" src="https://github.com/user-attachments/assets/bf780e0d-49c3-44cb-b8dc-65879ff54f10" />

---

## 🚨 Methodology 

### Phase 1: Lab Environment Deployment
- Configured a completely isolated, sandboxed virtual network environment utilizing Oracle VirtualBox.
- Deployed a pre-configured Kali Linux virtual machine to serve as the offensive testing workstation.
- Introduced an intentionally vulnerable Metasploitable 2 server appliance as the target host within the host-only private subnet.
- Verified local network routing and verified that both virtual systems could communicate exclusively with each other.

---

### Phase 2: Active Network Reconnaissance & Port Auditing
- Executed a comprehensive network footprinting scan across all 65,535 TCP ports utilizing Nmap.
- Targeted the system with aggressive service-version detection and operating system fingerprinting scripts.
- Launched Wireshark in the background to capture live packet data over the virtual network interface.
- Analyzed raw network traffic logs to study the structural mechanics of the TCP three-way handshake on exposed service sockets.

---

### Phase 3: Automated Vulnerability Assessment & Web Scanning
- Installed and initialized Tenable Nessus Essentials on the Kali Linux attack workstation.
- Configured and executed a network-wide automated scan against the Metasploitable 2 IP address to look for known security weaknesses.
- Cross-referenced open infrastructure services against the global CVE vulnerability database using the Nessus scanner engine.
- Deployed Nikto via the command line to specifically audit the target's web server configuration for missing HTTP security headers.

---

### Phase 4: Proxy Interception & Web Command Injection
- Opened the Damn Vulnerable Web Application (DVWA) in the browser to target input form elements.
- Configured Burp Suite to act as a local web proxy, routing all browser traffic through the interception tool.
- Trapped outbound HTTP POST request parameters within the Burp Suite Interceptor tab before they could reach the web server.
- Manually modified the raw form data by appending operating system shell command operators directly into the input parameters.

---

### Phase 5: Infrastructure Service Validation
- Targeted the exposed administrative Telnet service on port 23 by establishing a connection through the terminal.
- Attempted authentication by passing standard default engineering testing credentials directly into the cleartext login prompt.
- Initiated an unauthenticated connection request over port 21 to audit the File Transfer Protocol (FTP) service.
- Passed the default public anonymous username with a null/blank password argument to test administrative folder permissions.

---

---

## 📊 Key Findings Summary

| Vulnerability | Severity | Tool Used | Outcome |
|---------------|----------|-----------|---------|
| Command Injection (RCE) | Critical | Burp Suite & Firefox | Intercepted HTTP traffic and injected a semicolon operator (; whoami), forcing the web server to execute arbitrary system commands under the www-data account. |
| Bind Shell Backdoor | Critical | Tenable Nessus | Discovered an active root backdoor listening on an open network port, allowing anyone to attach to the terminal and instantly take full control without a password. |
| VNC Server Default Password | Critical | Tenable Nessus | Identified a remote desktop management service secured with the weak default credential "password", allowing total graphical session takeover. |
| Unencrypted Telnet Management | Medium | Linux Terminal & Nmap | Verified that the remote console management service sends all data in cleartext. Successfully logged into the server using default msfadmin testing credentials. |
| Anonymous FTP Access | Medium | Linux Terminal & Nmap | Connected to the file storage port using the username anonymous and a blank password, gaining unrestricted access to browse the server's internal files. |
| Missing HTTP Security Headers | Low / Info | Nikto | Discovered that the web server lacks X-Frame-Options and X-Content-Type-Options protections, leaving web users exposed to clickjacking and script injection. |

---

## 🧠 Learnings & Takeaways

- Understood the full VAPT lifecycle from scanning to exploitation
- Learned how outdated services (VSFTPd, Telnet) pose critical real-world risks
- Practiced responsible use of offensive security tools in a legal lab environment
- Gained familiarity with Metasploit, Burp Suite, Nessus, Nikto, and Wireshark
- Understood the importance of network segmentation and patch management

---

## 📎 Resources & Full Report

- 📄 **Full Report (PDF):** [View / Download](https://drive.google.com/file/d/1uC5W9rNINNeFap9-Nk1xJACGanR2YTij/view?usp=sharing)
- 🖼️ **Screenshot Gallery:** [Google Drive Folder](https://drive.google.com/drive/folders/1fxmKPafpcvMmfDs7c7vlQAyCKj0kyUi2?usp=sharing)

> The gallery includes additional screenshots and evidence not featured in the main report.

---

## 🤝Connect

**LinkedIn:** www.linkedin.com/in/yash-kumar-parmar  
**Email:** yashparmar.contact@gmail.com
```
