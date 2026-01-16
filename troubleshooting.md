## Incident #001 – PPP CHAP authentication failure

### Symptoms
- Serial interface up/down
- PPP configured on both sides
- Ping between R-HQ and R-ISP failed

### Investigation
- Verified interface status: `show interface serial0/3/0`
- Verified encapsulation: PPP
- Checked CHAP configuration on both routers
- Compared `username` and `hostname` values

### Root Cause
- Typographical error in the hostname of R-HQ
- CHAP authentication relies on exact hostname/username matching

### Resolution
- Corrected R-HQ hostname
- Re-tested PPP link
- Link status became up/up
- Ping successful

### Lessons Learned
- CHAP authentication is sensitive to hostname consistency
- Always verify identity parameters before assuming link failure

##

## Incident #002 – inter-VLAN communication not working

## Issue Description
Client devices successfully obtained IP addresses via DHCP and were able to reach their default gateways.  
However, **inter-VLAN communication was not working**.

---

## Observations
- DHCP was functional on all VLANs
- PCs could ping their respective default gateways
- Pings between different VLANs failed

---

## Troubleshooting Steps

### 1. VLAN Configuration Verification
- Confirmed that all required VLANs were created
- Verified that access ports were assigned to the correct VLANs

### 2. IP Addressing Verification
- PCs received valid IP addresses via DHCP
- Default gateways were correctly configured on client devices

### 3. SVI (Switch Virtual Interface) Verification
- VLAN interfaces (SVIs) were created for each VLAN
- Each SVI had a valid IP address
- All SVIs were in `up/up` state

### 4. Connectivity Testing
- Successful ping between PCs and their default gateways
- Failed ping between PCs located in different VLANs

---

## Root Cause
IP routing was not enabled on the Layer 3 switch.  
By default, a Layer 3 switch does **not** route traffic between VLANs unless IP routing is explicitly enabled.

---

## Resolution

Enabled IP routing on the Layer 3 switch:

```bash
ip routing
