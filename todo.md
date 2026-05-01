# Home Server Project - TODO

## Setup
- [x] Install Ubuntu Server on water damaged Lenovo laptop
- [x] Configure static IP via Netplan
- [x] Set up headless WiFi connection
- [x] Install and enable OpenSSH
- [x] Harden SSH - changed default port, key-based auth only
- [x] Install Docker
- [x] Configure NetworkManager as Netplan renderer
- [x] Connect server to GitHub via SSH
- [x] Fix default gateway to 192.168.1.254 (Eir F2000)
- [x] Update gateway4 to modern Netplan routes syntax
- [x] sudo apt upgrade -y (120 packages updated)
- [x] Fix SSH password auth (cloud-init override in sshd_config.d/)

## In Progress
- [ ] Document everything properly in this repo

## TODO
- [x] Redo new user exercise with proper SSH key setup
- [ ] Make battery conservation mode survive reboots (startup script)
- [ ] Set up WireGuard VPN
- [ ] Set up proper Docker usage
- [ ] Write a Dockerfile
- [ ] Use docker-compose for multi-container apps
- [ ] Configure Nginx as a reverse proxy
- [ ] Host something real on the server
- [ ] Set up AWS EC2 and mirror what is built locally
- [ ] Set up port forwarding to expose server to internet

## Learning Goals
- [x] Get comfortable with Linux basics
- [ ] Networking deep dive
- [ ] AWS certifications / study
- [ ] Prepare for Amazon Cloud Support Associate interview
