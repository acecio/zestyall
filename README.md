# StreamVault — Unified IPTV & Stream Hub

9 repos → 1 clean repo. All playlists auto-update via a single GitHub Actions workflow.

## Structure

```
.
├── .github/
│   └── workflows/
│       └── update-all.yml      # Single unified workflow
├── scripts/
│   ├── fancode.py              # FanCode 1080p M3U generator
│   ├── fancode-sayan.py        # FanCode via sayan/doctor-8trange source
│   ├── sony.py                 # Sony stream M3U + JSON
│   ├── jtv.py                  # Jio classic M3U from stream.json
│   ├── sayan.py                # Sayan IPTV M3U
│   ├── magnet.py               # Magnet channels M3U
│   ├── sportlink.py            # Sportlink M3U
│   ├── jiotv.py                # JioTV clearkey DRM M3U
│   ├── jiotv-mpd.py            # JioTV MPD stream M3U
│   ├── jio-playlist.py         # Jio from SECRET_JSON_URL
│   ├── desihub.py              # DesiHub scraper (BeautifulSoup)
│   ├── hitmaal-extract.js      # Hitmaal Playwright scraper
│   ├── ullu-extract.js         # Ullu Playwright scraper
│   └── alt-extract.js          # ALT Balaji Playwright scraper
├── playlists/
│   ├── jiotv.m3u
│   ├── jiotv-mpd.m3u
│   ├── playlist.m3u            # from SECRET_JSON_URL
│   ├── fancode.m3u
│   ├── fancode-sayan.m3u
│   ├── sony.m3u
│   ├── sonyliv.m3u
│   ├── jtv.m3u
│   ├── sayan.m3u
│   ├── magnet.m3u
│   └── sportlink.m3u
├── api/
│   ├── fancode.json
│   ├── sony.json
│   ├── sonyliv.json
│   ├── hitmaal-m3u8.json
│   ├── hitmaal-data.json
│   ├── ullu-m3u8.json
│   ├── alt-m3u8.json
│   └── desihub.json
├── meta/
│   └── jio-meta.txt            # JioTV channel metadata (logos, groups)
├── index.html                  # Vercel dashboard UI
├── vercel.json
├── package.json
└── .gitignore
```

## Setup

1. **Push to GitHub** — push this folder as a new repo

2. **Set secrets** — Go to repo Settings → Secrets and variables → Actions:
   - `SECRET_JSON_URL` — your private Jio JSON URL (for `playlist.m3u`)

3. **Enable Actions** — Go to the Actions tab and enable workflows

4. **Deploy to Vercel** — Import the repo on [vercel.com](https://vercel.com). The `index.html` at root serves as the dashboard.

5. **Deploy to Vercel** — Import the repo on [vercel.com](https://vercel.com). Dashboard at root `index.html` auto-renders.

## Raw Playlist URLs

After pushing, your playlists are at:
```
https://raw.githubusercontent.com/acecio/zestyall/main/playlists/jiotv.m3u
https://raw.githubusercontent.com/acecio/zestyall/main/playlists/fancode.m3u
https://raw.githubusercontent.com/acecio/zestyall/main/playlists/sony.m3u
# ... etc
```

## Update Schedule

| Job | Interval |
|-----|----------|
| Python Playlists | Every 15 min |
| SonyLIV Sync | Every 15 min |
| Playwright Scrapers | Every 30 min |
| DesiHub Scraper | Every 6 hours |
