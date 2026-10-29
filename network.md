# Networking Notes
Still no VLANs. Everything is on one flat network for now. It's on the list.

## Layout
- UniFi UDR7 does everything: router, gateway, DHCP, DNS, and it's the only AP
  - x.x.x.0/24, gateway x.x.x.1

## Addresses
| Host | IP | Notes |
|---|---|---|
| UDR7 | x.x.x.1 | Gateway + DNS |
| Proxmox (Beelink) | x.x.x.28 | |
| Valheim (CT 200) | x.x.x.50 | |
| TrueNAS (ZimaBoard) | x.x.x.133 | Everything hard-codes this one, needs to stay fixed |
| docker (CT 100) | x.x.x.216 | DHCP reservation, Jellyfin |

## DNS
- Pi-hole is retired. It was running as a TrueNAS app and UniFi DHCP handed it out to the whole house, not good for reliability
- Moved DNS back to the gateway before the pool rename so it wouldn't take the house down
  - UniFi DHCP DNS is back on Auto
  - Proxmox and TrueNAS both point at x.x.x.1, search domain `local`
  - CT 200 uses Tailscale's DNS
- Haven't turned on ad blocking on the UDR7 yet
- Pi-hole app is stopped. Delete it once I'm sure nothing still needs it

## Remote Access (Tailscale)
- No port forwards. Tailscale is the only way in from outside
- The Tailscale app on TrueNAS (`nas`) is the subnet router
  - Advertises x.x.x.0/24 and nothing else. No exit node
  - Accept routes is off (it's already on the LAN, accepting its own route would loop)
  - Catch: if the NAS is down, remote access is down too
- Replaced the default allow-all policy with real ACLs
  - Me: everything
  - My partner: Immich, Paperless, Homepage, Jellyfin and the SMB shares. Can't get to Proxmox, the TrueNAS UI or UniFi
  - Friends: Valheim only. CT 200 is its own tailnet node shared with them, it's not part of the subnet route, so they never see the LAN
- What's reachable remotely
  - Immich `nas:30041`
  - Paperless `nas:30070`
  - Homepage `nas:30054` (once it's installed)
  - Jellyfin `x.x.x.216:8096` through the route
- Checked from cellular with wifi off. Jellyfin works, Valheim friends can still connect

## Storage Traffic
- NFS for machines, SMB for people
- NFS uses UID/GID 3000 so the containers on Proxmox map cleanly
- Proxmox backups go to `tank/backups/proxmox` over NFS, export locked to x.x.x.28
  - vzdump every day at noon, all guests, keeps 3 daily / 1 weekly / 2 monthly
- CT 100 still mounts photos over NFS for the old Immich. That export goes away once I delete it

## VPN
- Proton VPN
  - Configured WireGuard client through UniFi Network.

## Todo
- [ ] VLANs: management, servers, clients, IoT. Get the homelab and game servers off the main LAN
- [ ] Inter-VLAN firewall rules (default deny)
- [ ] Ad blocking on the UDR7
- [ ] Make sure the NAS has a reservation at .133
