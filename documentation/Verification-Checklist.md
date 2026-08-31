# Verification Checklist

| Test | Expected Result |
|---|---|
| `show etherchannel summary` on AS-1 | Po1(SU), both members P |
| Remove one LACP cable | EtherChannel remains operational |
| `show spanning-tree vlan 10` | Redundant AS-2 path blocked/alternate |
| VLAN SVIs | VLAN 10/20/30/99 up/up |
| DHCP client test | Addressing from DHCP server |
| `show ip ospf neighbor` | FULL adjacency Core ↔ Edge |
| Core route table | OSPF default route via Edge |
| Edge route table | OSPF routes for VLAN 10/20/30/99 |
| `show ip nat translations` | PAT translations created |
| `show access-lists WAN-IN` | Inbound filtering counters |
| PC0 → 203.0.113.1 | Successful |
| PC1 → 203.0.113.1 | Successful |
