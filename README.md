# Homelab Infrastructure Project

## Overview

This project documents my personal homelab, built to develop practical Linux system administration, virtualization, web hosting, containerization, and infrastructure monitoring skills.

The environment runs on a Proxmox VE host with an Ubuntu Server virtual machine hosting several self-hosted services.

## Architecture

- **Proxmox VE:** Virtualization and VM management.
- **Ubuntu Server:** Linux server environment for hosting applications.
- **Nginx:** Web server hosting a local website.
- **Docker:** Container runtime for self-hosted applications.
- **Homepage:** Central dashboard linking to homelab services.
- **Jellyfin:** Self-hosted media streaming server deployed with Docker Compose.
- **Uptime Kuma:** Availability monitoring for infrastructure and applications.
- **Discord Webhooks:** Notifications for monitoring events.

## Services

| Service | Purpose |
|---|---|
| Proxmox VE | Virtual machine management |
| Nginx | Local website hosting |
| Homepage | Homelab service dashboard |
| Jellyfin | Self-hosted media streaming |
| Uptime Kuma | Service availability monitoring |
| Discord | Monitoring notifications |

## Monitoring Configuration

Five monitors were configured:

1. Homelab website — HTTP check.
2. Proxmox host — ping check.
3. Proxmox web interface — HTTPS check.
4. Homepage dashboard — HTTP check.
5. Jellyfin media server - HTTP check against its local web interface.

The monitors use a 60-second heartbeat interval and two retries to reduce false alarms from brief interruptions. Discord notifications were configured and tested successfully.

## Security Considerations

- Administrative interfaces are intended for trusted network access.
- Secrets, passwords, and webhook URLs must never be committed to Git.
- Configuration files and screenshots should be reviewed for sensitive information before publication.
- HTTPS certificate validation settings should be documented, including any exceptions made for a local self-signed certificate.
- Local HTTP services are not automatically protected by encryption.

## Skills Practiced

- Linux server administration
- Virtualization with Proxmox VE
- Web hosting with Nginx
- Docker container deployment
- YAML configuration
- Infrastructure monitoring and alerting
- Basic troubleshooting and service validation
- Technical documentation with Git and GitHub

## Future Improvements

- Document the network architecture.
- Add sanitized configuration examples.
- Expand monitoring coverage.
- Investigate secure HTTPS access for the website and dashboard.
- Explore backup and recovery procedures.
- Document future infrastructure and security improvements.
- Configure and document network media storage for Jellyfin.
- Test Jellyfin playback and media availability monitoring.

## Project Status

Initial deployment completed. Additional documentation and security improvements are ongoing.
