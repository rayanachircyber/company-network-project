# 🏢 Enterprise Campus Network – Cisco Packet Tracer

## 📌 Overview
This project models a real-world enterprise campus network using Cisco Packet Tracer, based on the **three-tier hierarchical model**:

- **Access Layer** – VLAN-based user connectivity  
- **Distribution Layer** – Inter-VLAN routing + redundancy (HSRP)  
- **Core/Edge Layer** – OSPF routing, GRE tunnel, and Internet access with NAT  

📂 Packet Tracer file: `packet-tracer/enterprise_network.pkt`

---

## 🧱 Architecture 

Access Switches (2960-XTT)  
│  
├── VLAN 10 → PCs (PC1, PC2)  
├── VLAN 20 → PCs (PC3, PC4)  
└── VLAN 30 → PCs (PC5, PC6)  
│  
▼  
Distribution Layer (L3 Switches)  
DSW1 (Active) —— DSW2 (Standby)  
│  
▼  
Router R1 —— GRE Tunnel —— Router R2 —— Access Switches (2960-XTT)—————— HTTP Server  
│--------------------------------- │---------------------------------------------------------├── TFTP Server  
--------------—Internet---------------------------------------------------------------------└── FTP SERVER  



---

## 📡 Protocols Used

| Layer | Protocol |
|------|----------|
| L2 | 802.1Q VLAN Trunking |
| L2 | STP (PVST) |
| L2 | CDP |
| L3 | IPv4 |
| L3 | OSPF |
| L3 | GRE Tunnel |
| L3 | HSRP |
| L3 | NAT (PAT) |
| L3 | ICMP (ping) |

---

## 🚀 How to Use
1. Open `enterprise_network.pkt` in Cisco Packet Tracer  
2. Navigate through devices and verify configurations  
3. Run connectivity tests between VLANs and WAN  

---

## 👤 Author  
**Rayan Achir**  
USTHB – Networking & Cybersecurity Student  






