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

## TODO
- [x] Redo new user exercise with proper SSH key setup
- [x] Make battery conservation mode survive reboots (startup script)
- [ ] Set up WireGuard VPN
- [x] Set up proper Docker usage
- [x] Write a Dockerfile
- [x] Use docker-compose for multi-container apps
- [x] Configure Nginx as a reverse proxy
- [x] Host something real on the server
- [x] Set up AWS EC2 and mirror what is built locally
- [x] Set up port forwarding to expose server to internet

## Cloud / AWS
- [x] Set up billing alarm (AWS Budgets)
- [x] Configure security groups (SSH + app port)
- [x] Allocate and associate Elastic IP for a stable public address
- [x] Diagnose and fix hardcoded path breaking docker-compose build on migration
- [ ] Buy a domain name and point it at the Elastic IP
- [ ] Set up HTTPS via Let's Encrypt/Certbot (needs domain first)
- [ ] Create a custom AMI from the working instance
- [ ] Set up an Application Load Balancer
- [ ] Set up an Auto Scaling Group (min/max instance limits)
- [ ] Load-test the scaling setup
- [ ] Learn Terraform basics — codify the EC2/security group/networking setup
- [ ] AWS Cloud Practitioner cert (after projects)

## CI/CD
- [x] Add GitHub Secrets for EC2 host/user/key
- [x] Write GitHub Actions workflow (deploy on push to main)
- [x] Test the pipeline end-to-end with a real deploy
- [ ] Add a build/lint check before deploy (basic CI, not just CD)

## Monitoring & Ops
- [ ] Set up Prometheus + Grafana
- [ ] Set up basic uptime/alerting for the live site

## Learning Goals
- [x] Get comfortable with Linux basics
- [x] Networking deep dive
- [x] Understand security groups vs router port forwarding
- [x] Understand AMI vs instance distinction
- [x] Understand CI/CD concepts (CI vs CD, GitHub Actions runners)
