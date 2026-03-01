# VirtualBox Cybersecurity Home Lab Documentation

## Purpose
The purpose of this document is to provide a comprehensive guide for setting up a cybersecurity home lab using VirtualBox. This lab is intended for continuous skill improvement following the completion of the TripleTen bootcamp.

## Lab Architecture Diagram
![Lab Architecture Diagram](link-to-diagram)

## Network Topology
- **Host:** Windows 11, Ryzen 9 3900X, 32GB RAM  
    - VirtualBox running the following VMs:

- **Kali Linux VM**  
    - RAM: 8GB  
    - CPUs: 4  
    - Tools: OpenVAS, Tenable Nessus  

- **pfSense Firewall**  
    - Operating System: Ubuntu  
    - RAM: 4GB  
    - CPUs: 2  

- **Snort IDS**  
    - Operating System: Ubuntu  
    - RAM: 4GB  
    - CPUs: 2  

- **Wazuh SIEM**  
    - Operating System: Ubuntu  
    - RAM: 8GB  
    - CPUs: 4  
    - Disk: 50GB SATA  
    - Agents: Installed on Host, Kali, and VirusTotal API integration  

- **Metasploitable 2**  
    - Operating System: BSD  
    - RAM: 4GB  
    - CPUs: 2  

- **Metasploitable 3**  
    - Operating System: Windows Server 2008  
    - RAM: 4GB  
    - CPUs: 2  

## Tools Overview
- **OpenVAS:** A full-featured vulnerability scanner.  
- **Tenable Nessus:** Professional vulnerability assessment solution.  
- **pfSense:** Open-source firewall/router software.  
- **Snort:** An open-source intrusion detection system (IDS).  
- **Wazuh:** A security monitoring solution. Supports SIEM integration.  

## Setup Instructions
1. Install VirtualBox on your Windows 11 host.
2. Create and configure the Kali Linux VM with specified resources.
3. Set up the pfSense firewall VM on Ubuntu.
4. Install the Snort IDS on a separate Ubuntu VM.
5. Deploy the Wazuh SIEM on Ubuntu with necessary configurations.
6. Configure Metasploitable 2 on BSD and Metasploitable 3 on Windows Server 2008.

## Lab Exercises
- Exercise 1: Scan the network using OpenVAS and Nessus.
- Exercise 2: Monitor network traffic with Snort.
- Exercise 3: Analyze security incidents using Wazuh.

## Security Considerations
- Ensure all VMs are properly isolated.
- Regularly update and patch all software.
- Implement strong password policies.

## Resources
- [VirtualBox Official Documentation](https://www.virtualbox.org/manual/ch01.html)
- [Kali Linux Documentation](https://www.kali.org/docs/)
- [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/)
- [Snort Documentation](https://www.snort.org/documents)
- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Metasploitable 2 Documentation](https://www.offensive-security.com/metasploit-unleashed/)
- [Metasploitable 3 Documentation](https://github.com/rapid7/metasploitable3)  

---
*Date Created/Updated: 2026-03-01 04:22:40 UTC*