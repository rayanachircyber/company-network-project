# 04 – Routing

Routing protocol:
- OSPF Area 0 used across:
  - Distribution ↔ Core links
  - GRE tunnel

R1 advertises default route to the campus.

## Routing to Servers (R2)

Router R2 advertises:
- 10.1.1.0/24 network into OSPF Area 0
- GRE tunnel network 172.16.1.0/30

Default route on R2:
ip route 0.0.0.0 0.0.0.0 101.1.1.2 

- NAT overload is used on Serial0/1/1: ip nat inside source list 10 interface Serial0/1/1 overload

