# 06 – Security

Basic security measures:
- VLAN separation
- Native VLAN not used for users
- Layer 3 routing only at Distribution

---
## R2 GRE Configuration

Tunnel interface:
- R2 Tunnel IP: 172.16.1.2/30  
- Tunnel source: Serial0/1/1 (101.1.1.1)  
- Tunnel destination: 100.1.1.1  

This allows:
- OSPF adjacency between R1 and R2
- Reachability from campus VLANs to servers
