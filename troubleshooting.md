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
