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

## 2. SSH Password Authentication Not Disabled
**Symptoms:** `PasswordAuthentication no` was set in sshd_config but passwords were still working. SSH keys were never actually being used despite thinking they were.

**Diagnosis:**
- `sudo sshd -T | grep passwordauthentication` — showed `yes` in live config despite sshd_config saying `no`
- `sudo grep -i "usepam" /etc/ssh/sshd_config` — showed `UsePAM yes` overriding the setting
- `ls /etc/ssh/sshd_config.d/` — revealed `50-cloud-init.conf`
- `sudo cat /etc/ssh/sshd_config.d/*` — showed `PasswordAuthentication yes` overriding main config

**Root Cause:** Ubuntu's cloud-init creates `/etc/ssh/sshd_config.d/50-cloud-init.conf` on first boot which overrides the main sshd_config. Files in `sshd_config.d/` take priority.

**Fix:** Changed `PasswordAuthentication yes` to `PasswordAuthentication no` in `/etc/ssh/sshd_config.d/50-cloud-init.conf`

**Bonus Issue:** Public key `id_ed25519.pub` was missing from PC entirely. Regenerated keypair with `ssh-keygen`, added new public key to `~/.ssh/authorized_keys` on server.

**Lesson:** Always verify live SSH config with `sudo sshd -T` rather than just reading sshd_config. Check `sshd_config.d/` for overrides. Ubuntu cloud-init will override your SSH settings by default.
