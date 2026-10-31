# Homelab Goals

## Objective
Build a reliable, segmented home server environment for learning systems, networking, and security.

---

## Architecture

### NAS
- OS: TrueNAS CE
- Role:
  - Primary storage
  - Runs the core apps (Immich, Paperless, Tailscale)
- Notes:
  - Focus on stability and data integrity
  - Laid out the same as client builds

### Mini PC
- OS: Proxmox
- Role:
  - Virtualization
  - Safe experimentation
  - Game servers

---

## Services

### Done
- [x] Docker (CT 1** on Proxmox, TrueNAS apps on the NAS)
- [x] DNS filtering. Ran Pi-hole for a while, moved DNS back to the UniFi gateway instead
- [x] Remote access over Tailscale instead of a WireGuard server
- [x] Proton VPN WireGuard client on UniFi
- [x] Immich, Paperless-ngx, Jellyfin

### Still want
- [ ] Homepage dashboard
- [ ] Ad blocking on the gateway
- [ ] n8n, AlbyHub
- [ ] Offsite backup

### Networking
- [ ] VLANs:
  - Management
  - Servers
  - Clients
  - IoT (future)
- [ ] Firewall:
  - Inter-VLAN rules (default deny, allow as needed)

---

## Security Goals
- Least privilege
- Network segmentation
- Minimal exposed services (nothing port forwarded, Tailscale only)
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
Storage and services are where I want them. Segmentation isn't started.
