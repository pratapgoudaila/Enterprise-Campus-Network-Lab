# Security Design

## WAN ACL

`WAN-IN` is applied inbound on Edge Router interface G0/3/0.

Policy:
1. Permit ICMP echo replies.
2. Permit TCP established traffic to the Edge public address.
3. Deny all other inbound IP traffic.

## Port Security

User and IT/Admin access ports use:
- Maximum 2 secure MAC addresses
- Sticky MAC learning
- Violation mode `restrict`
- PortFast

## SSH

Management access is configured for SSH on the switches. Telnet is not permitted on the primary VTY lines.

## Users VLAN Policy

`USERS-IN` defines the intended segmentation policy for VLAN 10:
- Block Users → IT/Admin
- Block Users → Management
- Permit other traffic after the explicit denies

Packet Tracer did not retain the SVI ACL attachment in this final build, so the policy is documented as configured policy rather than active enforcement.
