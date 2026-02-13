# 🛡️ Experience — VulNyx

![00](Screenshots/0.png)

---

## ℹ️ Information

The Experience machine exposes legacy SMB services on an unpatched Windows XP system, allowing remote code execution through the MS08-067 (CVE-2008-4250) vulnerability in the Windows Server service.

The vulnerable SMBv1 service enables a remote attacker to execute arbitrary code without prior authentication, completely compromising the integrity of the system.

From a real-world organizational perspective, this scenario represents:

- Critical exposure of legacy infrastructure

- Lack of patch management

- Use of insecure protocols

- High ransomware risk

The impact of this vulnerability is Critical, allowing remote execution with elevated privileges.

| Category | Details |
|:--------:|:-------:|
| Name | Experience |
| Platform | VulNyx |
| Difficulty | Easy |
| Operating System | Windows XP |
| Initial Attack Vector | SMBv1 – MS17-010 (EternalBlue) |
| Final Outcome | System Compromise |

---

## 📚 Scope & Methodology

The assessment was conducted following a structured approach, dividing the process into the following phases:

1. Controlled active reconnaissance  
2. Targeted enumeration of identified services  
3. Validation of known vulnerabilities  
4. Minimization of unnecessary noise during testing

---

## 🔍 Reconnaissance

As an initial step, a local network discovery scan was performed using `arp-scan` to identify active hosts within the same subnet.

![01](Screenshots/1.png)

This command sends ARP requests across the local network segment in order to detect live hosts responding at Layer 2. Unlike traditional ICMP-based discovery, ARP scanning is more reliable within local networks because it does not depend on firewall rules blocking ICMP traffic.

The scan identified an active host at:

- 192.168.1.139

- MAC Address: 08:00:27:1f:35:50

The MAC address prefix 08:00:27 is commonly associated with VirtualBox virtual machines, suggesting that the target system is running in a virtualized environment.

<div align="center">
  <img src="Screenshots/3.png" alt="Ping Result" width="700">
</div>

An ICMP echo request was sent to confirm host availability and network reachability.
The response confirmed that the target was alive, with a TTL value of 128, suggesting a Windows-based operating system.

This confirmed the presence of the target machine within the local network and provided the IP address required for further enumeration.

## 🔎 Enumeration

![02](Screenshots/2.png)



