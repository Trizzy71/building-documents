# Homelab Goals

## Objective
Build a reliable, segmented home server environment for learning systems, networking, and security.

---

## Planned Architecture

### NAS
- OS: TrueNAS CE
- Role:
  - Primary storage
  - Docker host for core services
- Notes:
  - Focus on stability and data integrity

### Mini PC
- OS: Proxmox
- Role:
  - Virtualization
  - Safe experimentation
- Notes:
  - Break things without risking core data

---

## Services to Deploy

### Containers
- Docker
- Planned services:
  - AdGuard or Pi-hole (DNS filtering)
  - WireGuard client (secure tunnel)
  - Media / utility containers as needed (Plex, n8n, AlbyHUB)

### Networking
- VLANs:
  - Management
  - Servers
  - Clients
  - IoT (future)
- Firewall:
  - Inter-VLAN rules (default deny, allow as needed)

---

## Security Goals
- Least privilege
- Network segmentation
- Minimal exposed services
- Encrypted traffic where possible

---

## Learning Focus
- Linux server administration
- Docker fundamentals
- Virtualization (Proxmox)
- DNS filtering
- VPN fundamentals
- Network segmentation

---

## Status
Completed (for now).
