# 05 – Network Services

Implemented services:
- HSRP for gateway redundancy
- OSPF for dynamic routing
- NAT overload for Internet access
 
## Centralized Services

All servers are centralized behind Router R2 in the 10.1.1.0/24 network:

- HTTP Server: 10.1.1.30  
- TFTP Server: 10.1.1.20  
- FTP Server: 10.1.1.10  

They are reachable from all campus VLANs via:
- OSPF + GRE tunnel
- R2 acting as gateway (10.1.1.1)
