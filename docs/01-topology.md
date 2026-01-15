# Network Topology

## Objective
Design the physical and logical topology of the enterprise network.

## Sites
- Headquarters (HQ)
- Branch Office

## Devices (HQ)
| Device       |   Model  |        Role       |
|--------------|----------|-------------------|
|     R-HQ     | 2911 |  WAN edge router  |
|  SW-HQ-Core  |   3560   | Core & L3 routing |
| SW-HQ-Access |   2960   |    Access layer   |

## Devices (Branch)
|    Device    |   Model  |      Role     |
|--------------|----------|---------------|
|     R-BR     |   2911 | Branch router |
| SW-BR-Access |   2960   |  Access layer |

## WAN Connectivity
- PPP + CHAP authentication
- Serial links
- HQ ↔ ISP: Point-to-point /30 link
- Branch ↔ ISP: Point-to-point /30 link
 
## ISP Role
- Transit routing only
- No NAT
- No DHCP
- No ACL filtering
- R-ISP : router 2901


    ## Interface Mapping

### HQ
- R-HQ Serial0/3/0 → R-ISP Serial0/3/0 (PPP / CHAP)
  - GigabitEthernet0/0 → SW-HQ-Core GigabitEthernet0/2

- SW-HQ-Core
  - Gi0/2 → R-HQ Gi0/0
  - Gi0/1 → SW-HQ-Access Gi0/1 (TRUNK)

### Branch
- R-BR Serial0/3/0 → R-ISP Serial0/3/1 (PPP / CHAP)
  - Gi0/1 → SW-BR-Access Gi0/1

## IP Planning
Refer to: docs/ip-planning.md
