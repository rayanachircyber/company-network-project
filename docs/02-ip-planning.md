# 02 – IP Addressing Plan

## VLAN Networks

| VLAN | Network | Gateway (HSRP) |
|------|---------|----------------|
| 10 | 192.168.10.0/24 | 192.168.10.100 |
| 20 | 192.168.20.0/24 | 192.168.20.100 |
| 30 | 192.168.30.0/24 | 192.168.30.100 |

## Inter-Router Links
- DSW1 ↔ R1: 10.10.10.0/30  
- GRE Tunnel: 172.16.1.0/30
 
## Server Network (Behind R2)

| Service | IP Address | Subnet |
|---------|------------|--------|
| HTTP | 10.1.1.30 | 10.1.1.0/24 |
| TFTP | 10.1.1.20 | 10.1.1.0/24 |
| FTP | 10.1.1.10 | 10.1.1.0/24 |

Default gateway on servers: **10.1.1.1 (R2)**
