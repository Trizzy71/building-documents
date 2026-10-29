# Homelab Journey

Personal documentation of my homelab build and cybersecurity learning.

## Focus
- Privacy
- Self-Sovereignty
- Networking
- Servers
- Practical, hands-on learning
- Most of all, knowledge! Progress!!

## Current Status
Active

Last push was Oct 2026. Renamed the pool `Main` to `tank` and redid the datasets to match the layout I use for client builds, moved Immich and Paperless onto TrueNAS, got rid of Pi-hole, and set up Tailscale. Network details in [network.md](network.md).

## My Mini-Rack (6in/8u)
- 6-inch rack design by Mauker (on MakerWorld)
  - GL.iNet Slate 7
    - WAN access
  - T-Mobile 5g Home internet (ew)
  - 3D-printed patch panel
    - So it's pretty
  - Beelink S12 Mini
    - Proxmox
      - CT 100 `docker`: Jellyfin (old Immich still here until I clean it up)
      - CT 103 Crafty Controller (Minecraft)
      - CT 200 Valheim server for friends, has its own Tailscale node
      - NixOS (VM)
    - Backs up all guests to the NAS daily

  - ZimaBoard 2
    - TrueNAS CE
      - 16GB RAM, boots off a 500GB SSD in a USB enclosure
      - Pool `tank`: ZFS mirror
        - 2x 8TB HDDs (~7.5TB usable)
        - family, users, photos, documents, backups, media, apps
        - Same layout as the T3 client builds so I can test my scripts on my own stuff first
      - Apps
        - Immich
        - Paperless-ngx
        - Tailscale (subnet router)
        - Excalidraw, IT-Tools
        - Homepage dashboard is next
        - SMB file shares for multiple users

- Standalone
  - UniFi UDR7
    - Router, DNS, only AP
  - External 8TB USB drive
    - Second copy of the NAS data

## Goals
- Clean, low-power homelab
  - 2.5 GbE internal networking
- Segmented layout (still not done)
- Real offsite backup
