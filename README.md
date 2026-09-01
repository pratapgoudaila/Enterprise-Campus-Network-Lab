# Enterprise Campus Network Lab

Cisco Packet Tracer enterprise campus lab demonstrating routing, switching, redundancy, NAT/PAT and basic network security.

## Main Technologies

- VLAN segmentation
- Inter-VLAN routing on a multilayer Core switch
- OSPF Area 100
- LACP EtherChannel
- PVST/STP redundancy
- Centralized DHCP with DHCP relay
- NAT overload/PAT
- WAN inbound extended ACL
- Users VLAN ACL policy definition
- SSH management
- Switch port security

## VLAN and IP Plan

| VLAN | Purpose | Subnet | Gateway |
|---|---|---|---|
| 10 | Users | 10.10.10.0/24 | 10.10.10.1 |
| 20 | IT/Admin | 10.10.20.0/24 | 10.10.20.1 |
| 30 | Servers | 10.10.30.0/24 | 10.10.30.1 |
| 99 | Management | 10.10.99.0/24 | 10.10.99.1 |

Other addressing:
- Core ↔ Edge: 10.255.255.0/30
- Core: 10.255.255.2
- Edge: 10.255.255.1
- Edge ↔ ISP: 203.0.113.0/30
- Edge: 203.0.113.2
- ISP: 203.0.113.1
- DHCP Server: 10.10.30.2
- AS-1 management: 10.10.99.11
- AS-2 management: 10.10.99.12
- PC0: 10.10.10.11
- PC1: 10.10.20.10

## Topology

ISP Router → Edge Router → Core L3 Switch → Access Switches → End Devices.

AS-1 uses two physical links to the Core in an LACP EtherChannel. AS-1 and AS-2 also have a redundant Layer-2 trunk used for STP failover.

## Verification Highlights

1. LACP bundle operational with both member links.
2. LACP behavior demonstrated after physically removing one member link.
3. STP redundant path observed between AS-1 and AS-2.
4. VLAN gateways verified as up/up.
5. DHCP relay uses 10.10.30.2.
6. OSPF adjacency reaches FULL between Core and Edge.
7. Core learns internal VLAN routes and an OSPF-learned default route.
8. WAN-IN ACL is applied inbound on the Edge WAN interface.
9. NAT/PAT provides Internet access for internal VLANs.
10. Both PC0 and PC1 successfully ping the ISP-side address 203.0.113.1.

## Security Note

`WAN-IN` is an active inbound ACL on the Edge WAN interface.

`USERS-IN` is defined as a Users VLAN segmentation policy. In this Packet Tracer build, the simulator did not retain the SVI ACL attachment, so it should not be represented as an active enforcement point in documentation.

The Users policy is intended to block:
- VLAN 10 → VLAN 20
- VLAN 10 → VLAN 99

## Project File

`Enterprise-Campus-Network-Lab.pkt`

## Screenshots

- `01-LACP-Both-Links-Up.png`
- `02-LACP-Physical-Link-Failure.png`
- `03-STP-Redundancy.png`
- `04-STP-Path-State.png`
- `05-STP-Failure.png`
- `06-STP-Recovery.png`
- `07-DHCP-Verification.png`
- `08-WAN-ACL-Verification.png`
- `09-InterVLAN-ACL-Users-Blocked.png`
- `10-NAT-MultiVLAN-Internet.png`


## Lab Disclaimer

This is a Cisco Packet Tracer learning/portfolio project. Some commands and behaviors differ from production IOS platforms.
