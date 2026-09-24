Home Server Project

A self-hosted infrastructure project that started on a water-damaged Lenovo laptop and now runs on AWS EC2 — built to learn real-world Linux administration, containerisation, and cloud deployment from the ground up.

Overview

This project documents the full journey of turning a spare laptop into a production-style server: hardening it, containerising a web stack with Docker, and migrating that stack to the cloud on AWS — all version-controlled and reproducible.

Stack: Ubuntu Server 24.04 · Docker & Docker Compose · Nginx (reverse proxy) · Flask (API backend) · AWS EC2

What's been built

Linux administration & hardening

Installed and configured Ubuntu Server 24.04 headless, with static networking via Netplan
SSH hardened to key-only authentication — password auth disabled entirely
New user provisioning with individual SSH key pairs
Automated battery conservation via a custom systemd service

Containerisation

Custom Nginx image built and configured as a reverse proxy
Flask API backend fully containerised
Multi-container orchestration with Docker Compose

Cloud deployment (AWS EC2)

Migrated the entire stack from bare-metal to an EC2 instance (Ubuntu 24.04, t3.micro, free tier)
Configured security groups as the cloud-native equivalent of router port forwarding
Diagnosed and fixed a hardcoded absolute path in docker-compose.yml that broke the build on migration — replaced with a relative path for true environment portability
Elastic IP configured for a stable, permanent public address

Version control

Entire project tracked in Git from day one, which is what made the EC2 migration possible with minimal changes to the codebase itself
Project structure
├── docker-project/       # Nginx reverse proxy, Flask app, Docker Compose config
├── server-project/       # Setup docs and troubleshooting notes
└── startupscript         # systemd battery conservation service
Running it locally
bash
cd docker-project
sudo docker-compose up -d

Static site served at /, Flask API reachable at /api, both proxied through Nginx on port 8000.

Why this project

Built as a hands-on way to learn infrastructure the way it's actually practiced — not just spinning up a tutorial, but hitting real problems (broken configs, networking quirks, portability bugs) and working through them from first principles.
