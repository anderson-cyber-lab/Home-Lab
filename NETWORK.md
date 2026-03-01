# Network Topology

This document outlines the detailed network topology for our lab environment.

## Topology Diagram

- **Router**: Cisco RV340
- **Switches**: Cisco SG250
- **Firewall**: pfSense

### Subnets
- **192.168.1.0/24**: Internal Network
- **192.168.2.0/24**: Management Network

## Firewall Configuration Rules

1. **Allow Internal Traffic**
   - Source: 192.168.1.0/24
   - Destination: Any
   - Action: Allow

2. **Allow Management Access**
   - Source: 192.168.2.0/24
   - Destination: 192.168.1.0/24
   - Action: Allow

3. **Block All External Access**
   - Source: Any
   - Destination: Any
   - Action: Deny

4. **Allow VPN Access**
   - Source: Any
   - Destination: 192.168.1.0/24
   - Action: Allow (only for VPN users)

### Conclusion

The above rules ensure a secure and segmented network environment that allows for flexibility while minimizing exposure to risks.