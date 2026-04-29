# Troubleshooting Stories

## 1. Gateway Misconfiguration
**Symptoms:** Server could receive SSH connections but had no outbound internet access. Could ping server from PC but server couldn't ping router or reach internet.

**Diagnosis:**
- `ping 8.8.8.8` — 100% packet loss
- `ping 192.168.1.1` — 100% packet loss  
- `arp -n` — revealed router had two IPs: 192.168.1.1 and 192.168.1.254
- `ping 192.168.1.254` — success, this was the real gateway

**Root Cause:** Netplan config had wrong default gateway set to 192.168.1.1. Eir F2000 router uses 192.168.1.254 as its actual gateway. 192.168.1.1 is just the admin page.

**Fix:** Changed `via: 192.168.1.1` to `via: 192.168.1.254` in `/etc/netplan/00-installer-config.yaml`

**Lesson:** Always verify the actual gateway IP before assuming 192.168.1.1. Inbound traffic to the server worked fine because local network traffic doesn't need the gateway — only outbound traffic does.
