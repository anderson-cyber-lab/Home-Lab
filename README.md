# VirtualBox Cybersecurity Home Lab

A comprehensive and continuously evolving cybersecurity home lab built with VirtualBox to practice and improve cybersecurity skills post-[TripleTen](https://tripleten.com/) bootcamp. This lab simulates a realistic network environment with multiple security tools, vulnerable servers, and monitoring systems for hands-on learning and skill development.

## 📋 Table of Contents

- [Purpose](#-purpose)
- [Lab Architecture](#%EF%B8%8F-lab-architecture)
- [Host Machine Specifications](#-host-machine-specifications)
- [Virtual Machines](#%EF%B8%8F-virtual-machines)
- [🌐 Network Topology](#-network-topology)
- [Tools & Technologies](#%EF%B8%8F-tools--technologies)
- [Lab Setup](#-lab-setup)
- [Usage & Labs](#-usage--labs)
- [Security Considerations](#-security-considerations)
- [Resources](#-resources)

---

## 🎯 Purpose

This home lab serves as a dedicated environment to:

- **Strengthen Cybersecurity Fundamentals**: Apply concepts learned during the TripleTen cybersecurity bootcamp
- **Hands-On Practice**: Conduct real-world scenarios including vulnerability assessment, penetration testing, and incident detection
- **Continuous Learning**: Experiment with new tools, techniques, and defensive strategies
- **Build Portfolio Projects**: Document findings and create case studies for professional development
- **Develop Lab Scenarios**: Create custom cybersecurity challenges and exercises
- **Network Security**: Understand network monitoring, intrusion detection, and threat hunting

---

## 🏗️ Lab Architecture

---

## 💻 Host Machine Specifications

| Component | Specification |
|-----------|---------------|
| **OS** | Windows 11 Pro/Enterprise |
| **Processor** | AMD Ryzen 9 3900X (12-core, 3.8-4.6 GHz) |
| **RAM** | 32 GB DDR4 |
| **Hypervisor** | Oracle VirtualBox (Latest Version) |
| **Storage** | SSD (recommended for optimal VM performance) |

---

## 🖥️ Virtual Machines

### 1. **Kali Linux** - Penetration Testing & Scanning
| Specification | Value |
|---------------|-------|
| **OS** | Kali Linux 2024.x |
| **RAM** | 8 GB |
| **CPU Cores** | 4 |
| **Disk** | 60+ GB |
| **Primary Role** | Offensive Security, Vulnerability Scanning |
| **Key Tools** | OpenVAS, Tenable Nessus, Metasploit Framework, Wireshark, Burp Suite, sqlmap, aircrack-ng |

**Purpose**: Primary attack platform for conducting vulnerability assessments, penetration tests, and exploitation exercises against vulnerable servers.

---

### 2. **pfSense** - Firewall & Network Security
| Specification | Value |
|---------------|-------|
| **OS** | pfSense (on Ubuntu Live Server) |
| **RAM** | 4 GB |
| **CPU Cores** | 2 |
| **Disk** | 20 GB |
| **Primary Role** | Network Firewall, Network Segmentation |
| **Key Features** | Packet filtering, VPN capabilities, traffic shaping, IDS/IPS integration |

**Purpose**: Acts as a gateway firewall to segment the lab network, control traffic between VMs, and simulate enterprise network policies.

---

### 3. **Snort** - Intrusion Detection System (IDS)
| Specification | Value |
|---------------|-------|
| **OS** | Snort (on Ubuntu Live Server) |
| **RAM** | 4 GB |
| **CPU Cores** | 2 |
| **Disk** | 30 GB |
| **Primary Role** | Network-based Intrusion Detection |
| **Key Features** | Packet analysis, signature-based detection, alert generation |

**Purpose**: Monitors network traffic for suspicious activity and generates alerts based on Snort rule signatures.

---

### 4. **Wazuh** - Security Information and Event Management (SIEM)
| Specification | Value |
|---------------|-------|
| **OS** | Wazuh (on Ubuntu Live Server) |
| **RAM** | 8 GB |
| **CPU Cores** | 4 |
| **Virtual Disk** | 50 GB SATA |
| **Primary Role** | Centralized Monitoring, Log Analysis, Threat Detection |
| **Agents** | Deployed on Host (Windows 11) and Kali Linux VM |
| **Integrations** | VirusTotal API Key configured |

**Purpose**: Central hub for collecting, analyzing, and correlating logs from all VMs and the host machine. Provides real-time alerting and threat intelligence through VirusTotal integration.

---

### 5. **Metasploitable 2** - Vulnerable Target (Linux)
| Specification | Value |
|---------------|-------|
| **OS** | Metasploitable 2 (on BSD) |
| **RAM** | 4 GB |
| **CPU Cores** | 2 |
| **Disk** | 20 GB |
| **Primary Role** | Intentionally Vulnerable Server |
| **Vulnerabilities** | Known exploitable services and misconfigurations |

**Purpose**: Purpose-built vulnerable Linux system for practicing exploitation techniques and refining penetration testing skills.

---

### 6. **Metasploitable 3** - Vulnerable Target (Windows)
| Specification | Value |
|---------------|-------|
| **OS** | Windows Server 2008 |
| **RAM** | 4 GB |
| **CPU Cores** | 2 |
| **Disk** | 30 GB |
| **Primary Role** | Intentionally Vulnerable Server |
| **Vulnerabilities** | Windows-specific exploitable services and CVEs |

**Purpose**: Purpose-built vulnerable Windows server for practicing Windows exploitation, privilege escalation, and lateral movement techniques.

---

## 🌐 Network Topology

The lab is configured with multiple virtual networks to simulate realistic network segmentation:

- **Management Network**: Host machine + Wazuh server
- **Production Network**: Kali Linux, pfSense, Snort
- **Target Network**: Metasploitable 2 & 3 (isolated from direct access)
- **Agent Communication**: Secure channels for Wazuh agents to report to central server

For detailed network configuration, see [NETWORK-TOPOLOGY.md](https://github.com/anderson-cyber-lab/Home-Lab/blob/main/NETWORK-TOPOLOGY.md)

---

## 🛠️ Tools & Technologies

### Security Tools
| Tool | Purpose | Deployed On |
|------|---------|-------------|
| **OpenVAS** | Vulnerability Scanning | Kali Linux |
| **Tenable Nessus** | Vulnerability Assessment | Kali Linux |
| **Metasploit Framework** | Exploitation Framework | Kali Linux |
| **Wireshark** | Network Traffic Analysis | Kali Linux |
| **Burp Suite** | Web Application Testing | Kali Linux |
| **Snort** | Network Intrusion Detection | Dedicated VM |
| **Wazuh** | SIEM & EDR | Dedicated VM with Agents |
| **VirusTotal API** | File Threat Intelligence | Wazuh Integration |

### Additional Components
- **Wazuh Agents**: Monitor host machine (Windows 11) and Kali Linux
- **VirusTotal API Key**: Integrated with Wazuh for malware detection and file analysis
- **pfSense Firewall**: Network traffic control and segmentation

---

## 🚀 Lab Setup

### Prerequisites
- VirtualBox installed on Windows 11 host
- Minimum 32 GB RAM available
- 300+ GB free disk space
- Stable internet connection for tool updates and downloads

### Initial Setup Steps

For detailed setup instructions, see [SETUP.md](https://github.com/anderson-cyber-lab/Home-Lab/blob/main/SETUP.md)

1. **Import Virtual Machines**
   - Download ISO/VM images for each machine
   - Create/import VMs with specified configurations

2. **Network Configuration**
   - Configure virtual networks in VirtualBox
   - Set up proper network adapters for each VM
   - Configure pfSense as gateway

3. **Tool Installation**
   - Install OpenVAS and Nessus on Kali Linux
   - Deploy Wazuh server and agents
   - Configure Snort rules and signatures

4. **Agent Configuration**
   - Deploy Wazuh agents on Windows 11 host
   - Deploy Wazuh agents on Kali Linux
   - Verify agent connectivity to Wazuh server

5. **Integration Setup**
   - Configure VirusTotal API key in Wazuh
   - Set up Snort alerts forwarding to Wazuh
   - Establish pfSense logging to Wazuh

---

## 📚 Usage & Labs

### Typical Lab Exercises

For specific lab scenarios and hands-on exercises, see [LABS.md](https://github.com/anderson-cyber-lab/Home-Lab/blob/main/LABS.md)

1. **Vulnerability Assessment**
   - Use OpenVAS/Nessus to scan Metasploitable targets
   - Document findings and severity ratings
   - Develop remediation strategies

2. **Penetration Testing**
   - Execute exploits from Metasploit Framework
   - Perform privilege escalation exercises
   - Practice lateral movement techniques

3. **Intrusion Detection**
   - Generate suspicious network traffic
   - Observe Snort alert generation
   - Review alerts in Wazuh dashboard

4. **Threat Hunting**
   - Analyze logs in Wazuh
   - Correlate events across multiple sources
   - Identify indicators of compromise (IOCs)

5. **Malware Analysis**
   - Test files with VirusTotal through Wazuh
   - Analyze network behavior during infection scenarios
   - Practice incident response procedures

---

## 🔒 Security Considerations

⚠️ **Important**: This lab is designed for isolated, local testing only.

- **Isolation**: Ensure lab network is completely isolated from production networks
- **Credentials**: Use strong, unique passwords for all VMs
- **Backups**: Maintain snapshots before conducting destructive tests
- **Monitoring**: Keep Wazuh active to detect unexpected behavior
- **Updates**: Intentionally keep vulnerable VMs unpatched for testing purposes
- **Host Security**: Maintain strong security on the Windows 11 host machine
- **No External Access**: Do not expose lab systems to the internet

---

## 📖 Documentation Links

- [SETUP.md](https://github.com/anderson-cyber-lab/Home-Lab/blob/main/SETUP.md) - VM configuration and installation instructions
- [NETWORK.md](https://github.com/anderson-cyber-lab/Home-Lab/blob/main/NETWORK.md) - Network topology and firewall configuration
- [AGENTS.md](https://github.com/anderson-cyber-lab/Home-Lab/blob/main/AGENTS.md) - Wazuh agent deployment and configuration guide
- [LABS.md](https://github.com/anderson-cyber-lab/Home-Lab/blob/main/LABS.md) - Lab scenarios and hands-on exercises
- [TROUBLESHOOTING.md](https://github.com/anderson-cyber-lab/Home-Lab/blob/main/TROUBLESHOOTING.md) - Common issues and solutions

---

## 📖 Resources

### Documentation
- [VirtualBox Official Documentation](https://www.virtualbox.org/wiki/Documentation)
- [Kali Linux Documentation](https://www.kali.org/docs/)
- [pfSense Documentation](https://docs.netgate.com/pfsense/)
- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Snort Documentation](https://snort.org/documents)

### Learning Resources
- [TripleTen Cybersecurity Bootcamp](https://tripleten.com/)
- [HackTheBox](https://www.hackthebox.com/)
- [TryHackMe](https://tryhackme.com/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)

### Tools & Frameworks
- [Metasploit Framework](https://www.metasploit.com/)
- [OpenVAS](https://www.openvas.org/)
- [Tenable Nessus](https://www.tenable.com/products/nessus)
- [VirusTotal](https://www.virustotal.com/)

---

## 🔄 Continuous Improvement

This lab is a living project that will evolve as skills develop:

- ✅ Regular updates to tools and configurations
- ✅ Documentation of new lab scenarios
- ✅ Experimentation with additional security tools
- ✅ Portfolio case studies from lab exercises
- ✅ Integration of new attack/defense techniques

---

## 📝 License

This documentation is provided as-is for personal educational purposes.

---

## 🤝 Contributing

This is a personal lab environment. Suggestions and improvements are welcome through documentation updates.
All credit goes to @JackedProgrammer on youtube for setup and how-to video series

---

**Last Updated**: 2026-03-01 04:33:02  
**Created By**: anderson-cyber-lab  
**Status**: 🟢 Active & Continuously Evolving

---

> "Security is a journey, not a destination. This lab is my playground for continuous learning and skill development in cybersecurity."
