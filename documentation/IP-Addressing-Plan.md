# IP Addressing Plan

| Segment | Network | Gateway | Notes |
|---|---|---|---|
| Users | 10.10.10.0/24 | 10.10.10.1 | VLAN 10 |
| IT/Admin | 10.10.20.0/24 | 10.10.20.1 | VLAN 20 |
| Servers | 10.10.30.0/24 | 10.10.30.1 | VLAN 30 |
| Management | 10.10.99.0/24 | 10.10.99.1 | VLAN 99 |
| Core-Edge transit | 10.255.255.0/30 | N/A | Core .2 / Edge .1 |
| Edge-ISP | 203.0.113.0/30 | N/A | Edge .2 / ISP .1 |

### Static/known hosts

- DHCP Server: 10.10.30.2
- AS-1: 10.10.99.11
- AS-2: 10.10.99.12
- PC0: 10.10.10.11
- PC1: 10.10.20.10
