## Container 1 for downloads/automation
This container handles all media automation, downloading, organizing, and streaming movies, series, and music.

---

## arrstack

The first arr stack has everything for automated movie and series downloading and streaming. The `musicarr` stack handles music. They share one torrent client (qBittorrent).

| Port | Service | Description |
|------|---------|-------------|
| `8096` | [Jellyfin](https://jellyfin.org/) | Self-hosted Netflix-like media streaming |
| `5055` | [Seerr](https://github.com/seerr-team/seerr) | Quick movie/series lookup & download requests |
| `8989` | [Sonarr](https://sonarr.tv/) | Automated TV series management |
| `7878` | [Radarr](https://radarr.video/) | Automated movie management |
| `9696` | [Prowlarr](https://prowlarr.com/) | Torrent indexer aggregator |
| `8080` | [qBittorrent](https://www.qbittorrent.org/) | Torrent client |
| `8191` | [FlareSolverr](https://github.com/FlareSolverr/FlareSolverr) | Cloudflare bypass proxy for indexers |

### Why Jellyfin?

Jellyfin is a free alternative to Plex, which used to be cheap but now costs $249.99 for a lifetime pass which is way too expensive for a self-hosted solution. Plex does have a free plan, but it lacks mobile app support (which makes it almost useless from the start) and doesn't include hardware transcoding. Hardware transcoding is actually the main reason I went with an Intel CPU, the UHD 730 handles it really well.

When I first looked at Jellyfin, I thought the UI was pretty ugly. But then I discovered there are a lot of plugins and themes, and now I'm really happy with how it looks.

<!-- TODO: Add Jellyfin screenshot here -->
<!-- ![Jellyfin Main Page](screenshots/jellyfin-main.png) -->

---

## musicarr

I started working on this long after I finished the first arr stack (hadn't touched it in almost a month). I thought why not try streaming MY music from MY server?

At first I considered using Jellyfin as my music streaming backend, but the more I dug into it, the more I realized Jellyfin's music streaming just isn't great. Then I found [Navidrome](https://www.navidrome.org/), which turned out to be perfect for my needs.

| Port | Service | Description |
|------|---------|-------------|
| `4533` | [Navidrome](https://www.navidrome.org/) | Self-hosted music streaming |
| `8686` | [Lidarr](https://lidarr.audio/) | Automated music management |
| `5030` | [Slskd](https://github.com/slskd/slskd) | Soulseek client for P2P music |
| `6595` | [Deemix](https://deemix.app/) | FLAC music downloads from Deezer |

### Where to get music

- **Lidarr + Prowlarr** — automated downloads from torrent trackers, but honestly there wasn't a lot of music on public trackers.
- **Deemix** — downloads FLAC files directly from Deezer. You need an active subscription for FLAC quality (free plan only gives you 128kbps MP3). I just used a free trial and downloaded everything I needed within a month.
- **Slskd** — a server-side Soulseek client. There's a lot of FLAC music available for free on the Soulseek network.

While I was downloading music I already knew, I ended up discovering way more new music than I expected. That was a nice bonus.

### Best Navidrome clients

I've tried a lot of Navidrome clients on iOS and PC. Here are the best ones:

- **PC:** [Feishin](https://github.com/jeffvli/feishin) — the best cross-platform desktop client.
- **iOS:** [Nautiline](https://nautiline.app/) — beautiful UI, tons of settings, 7-day free trial, and only $5 for a lifetime subscription. Highly recommend.
- **iOS (free):** [Amperfy](https://github.com/BLeeEZ/amperfy) — solid free client with a nice UI, but it lacks automatic lyrics downloading and feels a bit unintuitive compared to Nautiline.

---

## Storage & Hardware Notes

This container has a 4TB mount from my 10TB IronWolf drive — more than enough for movies, series, and my entire music library (which is just a bit over 100GB).

Since I don't have a backup drive... I just pray it doesn't randomly break on me.

---

## Container Details

- **Type:** LXC Container (Privileged)
- **OS:** Ubuntu
- **Storage mount:** `data-pool:subvol-100-disk-0` → `/media/storage` (4TB)
- **Orchestration:** Both stacks managed via Portainer

---

<!-- ## TODO / Plans -->
<!-- - [ ] Add Bazarr for automated subtitles -->
<!-- - [ ] Set up Recyclarr for TRaSH Guides quality profiles -->
