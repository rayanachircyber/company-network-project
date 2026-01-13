# VLAN Design

## Objective
Implement VLAN segmentation at the access layer.

## VLANs
| VLAN | Name | Purpose |
|----|------|--------|
| 10 | ADMIN | Admin department |
| 20 | HR | Human resources |
| 30 | IT | IT and servers |
| 40 | GUEST | Guest WiFi |

## Access Port Assignment
| Port | VLAN |
|----|----|
| Fa0/1 | 10 |
| Fa0/2 | 20 |
| Fa0/3 | 30 |

## Trunk Ports
| Port | Allowed VLANs |
|----|--------------|
| Gi0/1 | 10,20,30,40 |
| Fa0/10 | 30,40 |
