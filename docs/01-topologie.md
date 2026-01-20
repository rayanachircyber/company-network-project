# Network Topology

## Objective
Design and document a multi-site enterprise network with:
- Redundant campus switching
- Inter-VLAN routing (Layer 3)
- WAN connectivity using PPP
- Centralized routing and future scalability

---

## Sites Overview
- Headquarters (HQ)
- Branch Office (BR)
- ISP (Transit network)

---

## WAN Topology

### WAN Routers
| Device  | Model | Role |
|-------|-------|------|
| R-HQ   | 2911  | HQ Edge Router |
| R-ISP  | 2911  | ISP Transit Router |
| R-BR   | 2911  | Branch Edge Router |

### WAN Links
| Link | Interface | Encapsulation |
|----|----------|---------------|
| R-HQ ↔ R-ISP | Serial0/3/0 ↔ Serial0/3/0 | PPP |
| R-ISP ↔ R-BR | Serial0/3/1 ↔ Serial0/3/1 | PPP |

---

## HQ Campus Network

### Core / Distribution Layer
| Device | Model | Role |
|------|-------|------|
| SW-HQ-Core-1 | 3560-24PS | Multilayer Switch |
| SW-HQ-Core-2 | 3560-24PS | Multilayer Switch |

- Layer 3 routing enabled (SVI + OSPF)
- Redundant links to access layer
- Interconnected for resilience (future EtherChannel possible)

### Core Interconnections
| From | Interface | To | Interface | Type |
|----|-----------|----|-----------|------|
| SW-HQ-Core-1 | Fa0/3 | SW-HQ-Core-2 | Fa0/2 | Trunk |
| SW-HQ-Core-2 | Fa0/3 | SW-HQ-Core-1 | Fa0/2 | Trunk |

---

### Access Layer (HQ)

| Switch | Model | VLAN |
|------|-------|------|
| SW-Access-VLAN10 | 2960-24TT | VLAN 10 (ADMIN) |
| SW-Access-VLAN20 | 2960-24TT | VLAN 20 (HR) |
| SW-Access-VLAN30 | 2960-24TT | VLAN 30 (IT) |

#### Access Layer Connectivity
- Each access switch is dual-homed to both core switches
- All uplinks are configured as trunk ports

| Access Switch | Uplink Interface | Core Switch |
|-------------|-----------------|-------------|
| VLAN10 | Fa0/1 | SW-HQ-Core-1 |
| VLAN10 | Fa0/2 | SW-HQ-Core-2 |
| VLAN20 | Fa0/1 | SW-HQ-Core-1 |
| VLAN20 | Fa0/2 | SW-HQ-Core-2 |
| VLAN30 | Fa0/1 | SW-HQ-Core-2 |
| VLAN30 | Fa0/2 | SW-HQ-Core-1 |

---

### End Devices (HQ)

| VLAN | Device | Connected Switch |
|----|--------|------------------|
| 10 | PC1, PC2 | SW-Access-VLAN10 |
| 20 | PC3, PC4 | SW-Access-VLAN20 |
| 30 | PC5, PC6 | SW-Access-VLAN30 |

---

## Branch Network

### Branch LAN
| Device | Model | Role |
|------|-------|------|
| R-BR | 2911 | Branch Router |
| SW-BR-Access | 2960-24TT | Access Switch |

### Branch LAN Connectivity
| From | Interface | To | Interface |
|----|----------|----|-----------|
| R-BR | FastEthernet0/2/1 | SW-BR-Access | FastEthernet0/1 |

---

### Branch Servers
| Server | Purpose | Interface |
|------|--------|----------|
| Server0 | Application / Internal | SW-BR-Access Fa0/4 |
| Server1 | DNS / DHCP (optional) | SW-BR-Access Fa0/3 |
| Server2 | Backup / Test | SW-BR-Access Fa0/2 |

---

## Design Notes
- Inter-VLAN routing handled by multilayer switches at HQ
- WAN routing handled via OSPF (Area 0)
- Redundancy implemented at the switching layer
- Architecture ready for:
  - EtherChannel
  - HSRP
  - ACLs
  - NAT and VPN at edge routers

---

## Next Steps
- IP addressing plan
- OSPF configuration
- DHCP deployment
- NAT at HQ edge
- Security hardening
