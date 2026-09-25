<p align="center">
  <img src="https://play-lh.googleusercontent.com/k9OXcYUYd2Id7jSLB_Yf2EdgeeU9gdD5wS_0fe8Ze7jSPi5YI6St7ROKkS0QPM4jcg" width="90" height="90" alt="OTT EPG Guide Logo">
</p>

<h1 align="center">📺 OTT EPG Guide with Catch-Up</h1>

<p align="center">
  <b>Electronic Program Guide (EPG) resources for OTT & IPTV playlists</b><br>
  JioTV • Tata Play • ZEE5 • Sun NXT • SonyLIV
</p>

<p align="center">
  <img src="https://img.shields.io/badge/EPG-XMLTV-blue?style=for-the-badge" alt="EPG">
  <img src="https://img.shields.io/badge/Catch--Up-Supported-success?style=for-the-badge" alt="Catch-Up">
  <img src="https://img.shields.io/badge/Playlist-M3U-orange?style=for-the-badge" alt="M3U">
</p>

<p align="center">
  Compatible with applications such as <b>TiviMate</b>, <b>OTT Navigator</b> and other IPTV/OTT players supporting XMLTV EPG.
</p>

---

## 📖 About

**OTT EPG Guide with Catch-Up** provides XMLTV-compatible Electronic Program Guide data that can be linked to your IPTV/OTT playlists.

The EPG data can be used to display:

- 📺 Current and upcoming programs
- 🕐 Program schedules
- 🔄 Catch-up / replay information where supported
- 🏷️ Channel logos and metadata
- 📅 Multi-day programming information
- 🎬 Program descriptions and related metadata

Simply add the appropriate EPG URL to your playlist and match your channels using the correct `tvg-id`.

---

## ✨ Supported EPG Sources

| Platform     | EPG | Catch-Up | ID Format        |
| ------------ | :-: | :------: | ---------------- |
| 📡 JioTV     | ✅  |    ✅    | `144`            |
| 📡 Tata Play | ✅  |    ✅    | `ts840`          |
| 🎬 ZEE5      | ✅  |    —     | `0-9-zeetv`      |
| ☀️ Sun NXT   | ✅  |    —     | `sun9025`        |
| 🎥 SonyLIV   | ✅  |    —     | `sony1000009246` |

> **Note:** Catch-up availability depends on the source, channel and player implementation.

---

# 🔗 EPG LINKS

> **Tip:** Add one of the following URLs to your playlist using the `x-tvg-url` attribute.

### 1. 🌐 TS AIO OTT EPG

```text
https://avkb.short.gy/epg.xml.gz
```

Includes EPG data for supported OTT platforms.

---

### 2. 📡 JioTV — 2 Days EPG + Catch-Up

```text
https://avkb.short.gy/jioepg.xml.gz
```

Dedicated JioTV EPG with 2-day programming and catch-up support.

---

### 3. 📡 Tata Play — 2 Days EPG + Catch-Up

```text
https://avkb.short.gy/tsepg.xml.gz
```

Dedicated Tata Play EPG with 2-day programming and catch-up support.

---

# 🆔 TVG-ID FORMAT

Correct `tvg-id` mapping is essential for your player to associate a channel with its EPG data.

## JioTV

Use the channel ID directly:

```text
144
1918
291
```

Example:

```text
tvg-id="144"
```

---

## Tata Play

Prefix the channel ID with `ts`:

```text
ts840
ts842
ts521
```

Example:

```text
tvg-id="ts840"
```

---

## ZEE5

Use the following format:

```text
0-9-(id)
```

Example:

```text
tvg-id="0-9-zeetv"
```

---

## Sun NXT

Prefix the channel ID with `sun`:

```text
sun(id)
```

Example:

```text
tvg-id="sun9025"
```

---

## SonyLIV

Prefix the channel ID with `sony`:

```text
sony(id)
```

Example:

```text
tvg-id="sony1000009246"
```

---

# ⚙️ PLAYLIST CONFIGURATION

## Step 1 — Add the EPG URL

Add the EPG URL to the beginning of your M3U playlist:

```m3u
#EXTM3U x-tvg-url="https://avkb.short.gy/epg.xml.gz"
```

---

## Step 2 — Assign the Correct `tvg-id`

Each channel must use the ID that exists in the EPG XML.

For example:

```m3u
#EXTINF:-1 tvg-id="ts840" tvg-name="Shirdi Sai Baba" group-title="Spiritual",Shirdi Sai Baba
https://example.com/stream.mpd
```

For JioTV:

```m3u
#EXTINF:-1 tvg-id="144" tvg-name="Colors HD" group-title="Entertainment",Colors HD
https://example.com/stream.m3u8
```

---

# 📺 TATA PLAY EXAMPLE

```m3u
#EXTM3U x-tvg-url="https://avkb.short.gy/epg.xml.gz"

#KODIPROP:inputstream.adaptive.license_type=com.widevine.alpha
#KODIPROP:inputstream.adaptive.license_key=https://tataplay.live.ott.irdeto.com/Widevine/getlicense?CrmId=tatasky&AccountId=tatasky&ContentId=400000975&ls_session=YOUR_SESSION

#EXTINF:-1 tvg-id="ts840" tvg-logo="https://ltsk-cdn.s3.eu-west-1.amazonaws.com/jumpstart/Temp_Live/cdn/HLS/Channel/imageContent-56386-kfc14w60-v4/imageContent-56386-kfc14w60-m4.png" group-title="Spiritual",Shirdi Sai Baba
https://delta45tatasky.akamaized.net/out/i/554.mpd

#KODIPROP:inputstream.adaptive.license_type=com.widevine.alpha
#KODIPROP:inputstream.adaptive.license_key=https://tataplay.live.ott.irdeto.com/Widevine/getlicense?CrmId=tatasky&AccountId=tatasky&ContentId=400000976&ls_session=YOUR_SESSION

#EXTINF:-1 tvg-id="ts842" tvg-logo="https://ltsk-cdn.s3.eu-west-1.amazonaws.com/jumpstart/Temp_Live/cdn/HLS/Channel/imageContent-56389-kfdgngts-v3/imageContent-56389-kfdgngts-m3.png" group-title="Spiritual",Somnath Temple
https://delta45tatasky.akamaized.net/out/i/722.mpd
```

> ⚠️ Replace temporary/session-specific authentication values with your own valid credentials or session information.

---

# 📡 JioTV Example

```m3u
#EXTM3U x-tvg-url="https://avkb.short.gy/epg.xml.gz"

#EXTINF:-1 tvg-id="1918" group-title="Sports" tvg-language="English" tvg-logo="http://jiotv.catchup.cdn.jio.com/dare_images/images/Jio_Cricket_English.png",Jio Cricket English HD
http://localhost/jiotv/app/live.php?id=1918&e=.m3u8

#EXTINF:-1 tvg-id="144" group-title="Entertainment" tvg-language="Hindi" tvg-logo="http://jiotv.catchup.cdn.jio.com/dare_images/images/Colors_HD.png",Colors HD
http://localhost/jiotv/app/live.php?id=144&e=.m3u8

#EXTINF:-1 tvg-id="291" group-title="Entertainment" tvg-language="Hindi" tvg-logo="http://jiotv.catchup.cdn.jio.com/dare_images/images/Sony_HD.png",SET HD
http://localhost/jiotv/app/live.php?id=291&e=.m3u8
```

---

# 🧩 HOW EPG MATCHING WORKS

The basic relationship is:

```text
M3U Playlist
     │
     ├── tvg-id
     │      │
     │      ▼
     │   XMLTV EPG
     │      │
     │      ▼
     └── Channel Program Guide
```

For example:

```text
Playlist
   │
   └── tvg-id="144"
            │
            ▼
       EPG XML
            │
            ▼
       JioTV Channel
            │
            ▼
       Program Schedule
```

The `tvg-id` in your playlist must match the corresponding channel ID in the EPG source.

---

# 🛠️ TROUBLESHOOTING

### EPG is not showing

Check the following:

- ✅ EPG URL is reachable
- ✅ `x-tvg-url` is correctly written
- ✅ `tvg-id` exactly matches the XMLTV channel ID
- ✅ Playlist has been refreshed
- ✅ Your IPTV player supports XMLTV
- ✅ The EPG source contains data for the requested channel

### Channel appears but no program guide

Usually this means the `tvg-id` does not match.

For example:

```text
EPG ID:
144
```

Your playlist should contain:

```text
tvg-id="144"
```

Not:

```text
tvg-id="144 "
tvg-id="Jio144"
tvg-id="jio144"
```

unless those IDs actually exist in the EPG source.

---

# 📱 PLAYER COMPATIBILITY

The EPG is intended for IPTV/OTT players supporting XMLTV-compatible EPG data.

Examples include:

- TiviMate
- OTT Navigator
- Kodi-based IPTV players
- Other M3U/XMLTV-compatible players

Actual feature availability may vary between applications.

---

# ⚠️ DISCLAIMER

This project/documentation is provided for **educational and informational purposes only**.

- Do not use the information to access content without proper authorization.
- Respect the terms of service of the relevant streaming providers.
- Do not redistribute copyrighted content without permission.
- Do not use this documentation for unauthorized commercial distribution.
- Users are responsible for how they configure and use their playlists and EPG sources.

---

# 💖 Credits

This documentation and the original project were created and maintained by **TechieSneh**.

Please respect the original attribution and do not remove or modify the project credits when redistributing the documentation.

<p align="center">
  <b>© 2021-26 TechieSneh</b>
</p>

<p align="center">
  Made with ❤️ for the OTT / IPTV community
</p>

<!-- DO NOT REMOVE THIS CREDIT -->

<!-- © 2021-26 TechieSneh -->
