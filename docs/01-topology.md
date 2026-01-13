# Network Topology

## Objective
Design the physical and logical topology of the enterprise network.

## Sites
- Headquarters (HQ)
- Branch Office

## Devices (HQ)
| Device       |   Model  |        Role       |
|--------------|----------|-------------------|
|     R-HQ     | ISR 2911 |  WAN edge router  |
|  SW-HQ-Core  |   3560   | Core & L3 routing |
| SW-HQ-Access |   2960   |    Access layer   |

## Devices (Branch)
|    Device    |   Model  |      Role     |
|--------------|----------|---------------|
|     R-BR     | ISR 2911 | Branch router |
| SW-BR-Access |   2960   |  Access layer |

## WAN Connectivity
- HQ ↔ ISP: Point-to-point /30 link
- Branch ↔ ISP: Point-to-point /30 link
