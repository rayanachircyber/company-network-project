# 01 – Network Topology

The network consists of:

## Access Layer
- 3 x Cisco 2960 switches  
- Each switch serves one VLAN:
  - Switch0 → VLAN 10
  - Switch1 → VLAN 20
  - Switch2 → VLAN 30

## Distribution Layer
- Two Layer 3 switches:
  - DSW1 (Active)
  - DSW2 (Standby)
- Connected in a redundant mesh

## Core / WAN
- Router R1 connected to DSW1/DSW2
- GRE tunnel between R1 and R2
- Internet simulated via serial link

## 🖥️ Servers & Services

The network includes three centralized servers located in the 10.1.1.0/24 network behind **Router R2**:

| Service | IP Address | Router |
|---------|------------|--------|
| HTTP | 10.1.1.30 | R2 |
| TFTP | 10.1.1.20 | R2 |
| FTP | 10.1.1.10 | R2 |

These servers are reachable from the campus through:
- OSPF routing
- GRE tunnel
- NAT on R2 for Internet-bound traffic

