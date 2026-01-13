# IP Addressing Plan

## HQ VLANs
| VLAN | Department | Subnet | Gateway |
|----|-----------|--------|--------|
| 10 | Admin | 192.168.10.0/24 | 192.168.10.1 |
| 20 | HR | 192.168.20.0/24 | 192.168.20.1 |
| 30 | IT | 192.168.30.0/24 | 192.168.30.1 |
| 40 | Guest WiFi | 192.168.40.0/24 | 192.168.40.1 |

## Branch LAN
| Network | Subnet | Gateway |
|------|--------|--------|
| Branch Users | 192.168.50.0/24 | 192.168.50.1 |

## WAN Links
| Link | Subnet |
|----|--------|
| HQ – ISP | 10.0.0.0/30 |
| ISP – Branch | 10.0.0.4/30 |
