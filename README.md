# AntiX Nettop Media Center Client Setup

An Ansible playbook designed to automatically provision and configure a lightweight Linux nettop (specifically tailored for **antiX Linux** or Debian-based minimal distributions) as a dedicated media center client.

This configuration focuses on resource efficiency by deploying minimal dependencies, optimizing audio/video access for a non-root user, and establishing core network security metrics.

## Features

- **Resilient Package Management:** Runs system cache updates with automated retry logic (`until/retries`) to handle network drops.
- **Lightweight Media Stack:** Installs `mpv` (highly efficient CLI/GUI media player) along with critical system utilities (`curl`, `alsa-utils`, `htop`).
- **User Privilege Management:** Grants the target user access to hardware acceleration and sound devices by modifying `audio` and `video` groups without altering existing memberships.
- **Environment Skeleton:** Automates creation of a localized script path (`~/bin`) with proper executable permissions (`0755`).
- **Uncomplicated Firewall (UFW) Integration:** Secures the network perimeter by enabling the firewall and explicitly permitting ingress `OpenSSH` traffic to prevent accidental lockout.

## Prerequisites

Before executing this playbook, ensure you have:

1. Ansible installed on your control machine (e.g., your primary workstation or homelab controller).
2. SSH access to the target nettop with key-based authentication.
3. Sudo privileges configured on the target host for administrative overrides.

## Directory Structure

```text
.
├── playbook.yml          # The core Ansible automation instructions
├── hosts.txt             # Target host topology configurations (Do not commit real IPs)
└── README.md             # Project documentation
