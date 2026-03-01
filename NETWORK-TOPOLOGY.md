# Network Topology Diagram and Configuration

## Overview
This document outlines the detailed network topology and configuration of the home lab environment. The network has two primary segments:
1. **Bridged Network** (192.168.0.0/24)
2. **Isolated Internal Network** (172.30.2.0/24)

### Bridged Network (192.168.0.0/24)
- **Devices:**
  - Kali Box
  - Wazuh Server
  - Host Machine (Windows 11)
- **Connectivity:**
  - Connects these devices to the outside network and each other.

### Isolated Internal Network (172.30.2.0/24)
- **Devices:**
  - pfSense Firewall
  - Snort IDS
  - Metasploitable 2
  - Metasploitable 3
- **Connectivity:**
  - Only devices in this range can communicate with each other.

### Device Network Configuration
| Device               | IP Address       | Network Segment              |
|----------------------|------------------|-------------------------------|
| Kali Box             | 192.168.0.10     | Bridged Network               |
|                      | 172.30.2.10      | Isolated Internal Network      |
| Wazuh Server         | 192.168.0.11     | Bridged Network               |
|                      | 172.30.2.11      | Isolated Internal Network      |
| Host Machine (Win11) | 192.168.0.12     | Bridged Network               |
| pfSense Firewall     | 172.30.2.1       | Isolated Internal Network      |
| Snort IDS            | 172.30.2.2       | Isolated Internal Network      |
| Metasploitable 2     | 172.30.2.3       | Isolated Internal Network      |
| Metasploitable 3     | 172.30.2.4       | Isolated Internal Network      |

### Connectivity Matrix
| Source              | Destination       | Ping Test Result  |
|---------------------|-------------------|-------------------|
| Kali Box            | Wazuh Server      | Successful         |
| Kali Box            | Host Machine      | Successful         |
| Kali Box            | pfSense Firewall   | Failed             |
| Kali Box            | Snort IDS         | Failed             |
| Kali Box            | Metasploitable 2  | Failed             |
| Kali Box            | Metasploitable 3  | Failed             |
| Wazuh Server        | Host Machine      | Successful         |
| Wazuh Server        | pfSense Firewall   | Failed             |
| Wazuh Server        | Snort IDS         | Failed             |
| Wazuh Server        | Metasploitable 2  | Failed             |
| Wazuh Server        | Metasploitable 3  | Failed             |
| Host Machine        | pfSense Firewall   | Failed             |
| Host Machine        | Snort IDS         | Failed             |
| Host Machine        | Metasploitable 2  | Failed             |
| Host Machine        | Metasploitable 3  | Failed             |
| pfSense Firewall    | Snort IDS         | Successful         |
| pfSense Firewall    | Metasploitable 2  | Successful         |
| pfSense Firewall    | Metasploitable 3  | Successful         |
| Snort IDS           | Metasploitable 2  | Successful         |
| Snort IDS           | Metasploitable 3  | Successful         |
| Metasploitable 2    | Metasploitable 3  | Successful         |

### ASCII Art Diagram
```
       +-----------------------+        +---------------------+
       |  Kali Box            |        |  Windows 11        |
       |  192.168.0.10       |        |  192.168.0.12     |
       +-----------------------+        +---------------------+
                |                                    |
                |                                    |
                |                                    |
      +-----------------------+                      |
      |  Wazuh Server        |                      |
      |  192.168.0.11       |                      |
      +-----------------------+                      |
                |                                    |
                |                                    |
                |                                    |
     +------------------------------------+          |
     |           Bridged Network         |          |
     |           192.168.0.0/24           |          |
     +------------------------------------+          |
                |                                    |
                |                                    |
                |                                    |
      +-----------------------+                      |
      |  pfSense Firewall    |                      |
      |  172.30.2.1         |                      |
      +-----------------------+                      |
                |                                    |
      +---------+---------+                            |
      |         |         |                            |
      |         |         |                            |
+-----+       +-----+   +-----+            +---------+         
| Snort |     | Metasploit 2   |     | Metasploit 3    |  
| 172.30.2.2 | 172.30.2.3 |   | 172.30.2.4   |
+-----+       +-----+   +-----+

```