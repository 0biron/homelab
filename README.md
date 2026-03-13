# obiron's homelab

This is my public archive of everything I've built so far. (No AI slop here, EVERYTHING WAS WRITTEN BY ME, AI JUST HELPED WITH REFINING AND FORMATTING)

This is my first experience with self-hosting, picking parts for a server build, system management, etc. I've been daily-driving Linux for over a year, which made the whole process surprisingly smooth. The best part about all of this is that you control everything that you own (if you buy digital media) or download from torrents. You own your media - no more depending on predatory services like Netflix or Spotify to decide what you can watch or listen to.

AI has been a huge helper throughout this project, from debugging issues to discovering great iOS client apps. I've been using Gemini 3 Pro heavily and it boosted both my productivity and learning by a mile. (don't trust any AI. think before doing anything significant! HAVE YOUR OWN HEAD)

Overall the coolest thing about this project is free and unlimited Google Photos storage backup (it's written down in the VM2 part).

I'll keep updating this repo with new services as I add them. If you stumble upon it - feel free to star it and share with a friend, I'd really appreciate it :)

---
My self-hosted infrastructure journey — started mid-December 2025.
Built on **Proxmox** with LXC containers running Docker, VMs via **Portainer**.

---

## 📦 Container 1 — Media/Arr

### `arrstack` — Movies, Series & Torrents🎥

| Port | Service | Description |
|------|---------|-------------|
| `8096` | [Jellyfin](https://jellyfin.org/) | Self-hosted Netflix-like media streaming |
| `5055` | [Seerr](https://github.com/seerr-team/seerr) | Quick movie/series lookup & download requests |
| `8989` | [Sonarr](https://sonarr.tv/) | Automated TV series management |
| `7878` | [Radarr](https://radarr.video/) | Automated movie management |
| `9696` | [Prowlarr](https://prowlarr.com/) | Torrent indexer aggregator |
| `8080` | [qBittorrent](https://www.qbittorrent.org/) | Torrent client |
| `8191` | [FlareSolverr](https://github.com/FlareSolverr/FlareSolverr) | Cloudflare bypass proxy for indexers |

### `musicarr` — Music Streaming & Downloads
**Really recommend** you try this *arr stack out! I really enjoyed the process of setting it up and exploring new music while doing so :)
It works like a full streaming service (especially if you use Nautiline as your client), but you need to buy your own music. Alternatively, you can use Deemix for downloading FLAC songs for free (just use a free trial on Deezer and download all the music you want), and you can find a lot of free/indie music on Slskd. You can also use Lidarr for downloading music from torrent clients, but I haven't found a lot of good music trackers.
| Port | Service | Description |
|------|---------|-------------|
| `4533` | [Navidrome](https://www.navidrome.org/) | Self-hosted music streaming |
| `8686` | [Lidarr](https://lidarr.audio/) | Automated music management |
| `5030` | [Slskd](https://github.com/slskd/slskd) | Soulseek client for P2P music |
| `6595` | [Deemix](https://deemix.app/) | FLAC music downloads from Deezer |

---

## 📦 Container 2 — Cloud storage & Management

| Port | Service | Description |
|------|---------|-------------|
| `9443` | [Portainer](https://www.portainer.io/) | Docker container management UI |
| `2283` | [Immich](https://immich.app/) | Self-hosted Google Photos replacement |
| `8080` | [Nextcloud](https://nextcloud.com/) | Self-hosted Google Drive replacement |
| `5230` | [Memos](https://www.usememos.com/) | Lightweight self-hosted notes(really enjoy using memos) |
| `3000` | [Homepage](https://gethomepage.dev/) | Services dashboard |
| `5984` | [CouchDB](https://couchdb.apache.org/) | Database backend for Obsidian LiveSync |
| `8765` | [Speedtest](https://github.com/librespeed/speedtest) | Automated network speed testing |

---

## 📦 VM1 — Home Assistant

| Port | Service | Description |
|------|---------|-------------|
| `8123` | [Home Assistant](https://www.home-assistant.io/) | Just Home Assistant(will add details soon) |

---
## 📦 VM2 — Ubuntu Android
 
Free offsite backup of Immich photos → Google Photos using [Redroid](https://github.com/remote-android/redroid-doc) (Android 11 in Docker) + [Google Photos ReVanced](https://github.com/Unofficial-Life/revanced-gphotos-build/releases/tag/9) for free unlimited storage.

Immich library(read-only) is SMB-mounted into the VM, bind-mounted into Redroid, and Google Photos backs it up automatically. A daily cron job triggers media rescans to pick up new photos.
INFINITE FREE STORAGE FOR BACKUP🥳🥳
 
| Component | Role |
|-----------|------|
| [Redroid](https://github.com/remote-android/redroid-doc) | Android 11 in Docker (`5555` ADB) |
| [Google Photos ReVanced](https://github.com/Unofficial-Life/revanced-gphotos-build/releases/tag/9) | Modded Google Photos — free unlimited storage |
| [GmsCore (microG)](https://github.com/ReVanced/GmsCore) | Google account access for ReVanced |
| [scrcpy](https://github.com/Genymobile/scrcpy) | Screen mirroring for initial setup |

---

## 📱 Client Apps (iOS / TV)
I've tested a ton of client apps and written down the best ones below - you won't regret trying any of them (though some are paid). **THEY ARE THE BEST**
| App | Description |
|-----|-------------|
| [ProxMobo](https://proxmobo.app/) | Great Proxmox machine iOS manager |
| [Yomo](https://apps.apple.com/us/app/yomo-docker-portainer/id6479982236) | Managing **Docker** / **Portainer** containers from iOS |
| [MoeMemos](https://github.com/mudkipme/MoeMemos) | **Memos** native client for iOS |
| [Feishin](https://github.com/jeffvli/feishin) | Perfect **Navidrome** cross-platform (PC only) music player |
| [Nautiline](https://nautiline.app/) | The best iOS **Navidrome** player — beautiful UI, full-featured · $5 lifetime(JUST BUY IT ONCE AND FORGET ABOUT SPOTIFY) |
| [Amperfy](https://github.com/BLeeEZ/amperfy) | **Nautiline** equivalent but **free** on iOS, fewer features, lyrics broken |
| [Swiftfin](https://github.com/jellyfin/Swiftfin) | The best iOS **Jellyfin** player |
| [Moonfin](https://github.com/nicholasgasior/moonfin) | **Seerr + Jellyfin** in one app on Tizen OS · installed via [Jellyfin2Samsung](https://github.com/nicholasgasior/Samsung-Jellyfin-Installer) |
| [qRemote](https://apps.apple.com/us/app/qremote-for-qbittorrent/id6756276747) | Easy-to-use iOS **qBittorrent** client |
| [Ruddarr](https://github.com/ruddarr/app) | Managing **Radarr** / **Sonarr** from iOS |
| [Pocket](https://apps.apple.com/in/app/pocket-for-seerr/id6746105104) | A beautiful iOS app for **Seerr** |

---

## 🛠️ Tech Stack

- **Hypervisor:** Proxmox VE
- **Containers:** LXC + Docker + VM
- **Orchestration:** Portainer
- **Notes:** Obsidian (synced via CouchDB LiveSync) / Memos
- **Network:** MiWifi router / Tailscale runs on the main PVE node and makes all LXC container IPs and ports accessible via the Tailscale network.

---
## 🖥 Server Specs

- **CPU:** 12th Gen Intel(R) Core(TM) i5-12400
- **GPU:** Intel UHD Graphics 730(best for fast video transcoding)
- **Motherboard:** Asus Prime B660M-K D4
- **RAM:** 32 GB (2х16 Kingston Fury DDR4-3200)
- **Storage(Boot drive):** SSD M2 NVMe 512Gb 
- **Storage:** IronWolf 10tb NAS
- **Case:** Fractal Design Define R4

You probably don't need a PC as beefy as mine for a home server, but since this is my first build I went with extra headroom for the future. The whole thing cost me around ~$449 (~20,000 UAH), and to this day I haven't regretted a single dollar. Pretty great value for what it does, and it will pay for itself in 1–2 years of not paying for iCloud, Netflix, and Spotify (not including the electricity bill - this build only draws around 20W idle).

---
## 📝 Roadmap

- [ ] Reverse proxy (Nginx Proxy Manager / Caddy)
- [ ] Custom domain with SSL
- [ ] Buy 2.5G/10G switch and 2× 2.5G network cards
- [ ] Finish the roadmap

---

<p align="center">
  <i>AI helped me with refining this README, but everything here was written by me - AI just helped with formatting</i>
</p>
