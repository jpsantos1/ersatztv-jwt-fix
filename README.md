# ErsatzTV (Community Fork)

ErsatzTV lets you transform your media library into a personalized, live TV experience — complete with EPG, channel scheduling, and seamless streaming to all your devices.

This repository is a **community-maintained fork** of the original ErsatzTV project, which is currently archived.

It includes fixes and improvements to keep the project usable in modern setups.

[![contact](https://img.shields.io/badge/contact_us-510b80?style=for-the-badge)](https://ersatztv.org/contact)
[![features](https://img.shields.io/badge/vote_on_features-darkgreen?style=for-the-badge)](https://features.ersatztv.org/)
[![community](https://img.shields.io/badge/join_the_community-blue?style=for-the-badge)](https://discuss.ersatztv.org)

![epg-example](https://ersatztv.org/images/home/epg-example.png)

---

# Important Notice

The original ErsatzTV repository has been **archived** and is no longer actively maintained.

This fork exists to:

- maintain compatibility with modern environments
- fix bugs affecting real-world deployments
- continue improving the project for the community

All credit for the original work belongs to the ErsatzTV maintainers and contributors.

---

# Fixes in this Fork

### JWT + HLS Streaming Fix

When JWT authentication is enabled (`JWT__ISSUERSIGNINGKEY`), HLS players request the playlist with an `access_token` query parameter.

However, the original implementation generated segment URLs without propagating this token.

Example before:
/iptv/hls-direct/1.ts?index=1


This caused segment requests to fail with:


401 Unauthorized


Example after:


/iptv/hls-direct/1.ts?index=1&access_token=TOKEN


This change allows authenticated playback with IPTV and HLS players that do not support sending Authorization headers for segment requests.

Tested successfully with:

- IPTV Smarters
- HLS players
- JWT-protected IPTV streams

---

# How It Works

1. **Install ErsatzTV**: Download and set up the server on your system.
2. **Add Your Media**: Connect your media libraries and collections.
3. **Create Channels**: Design and schedule your own live channels.
4. **Stream Anywhere**: Watch on any device with IPTV and EPG support.

---

# Key Features

- **Custom channels**: Create and schedule your own live TV channels.
- **IPTV & EPG**: Stream with IPTV and Electronic Program Guide support.
- **Hardware Transcoding**: High-performance streaming with hardware acceleration (NVENC, QSV, VAAPI, AMF, VideoToolbox)
- **Media Server Integration**: Connect Plex, Jellyfin, Emby and more.
- **Music & Subtitles**: Mix music videos and enjoy subtitle support.
- **Open Source**: Free, open, and community-driven project.

---

# Documentation

Documentation is available at:

https://ersatztv.org/docs/

---

# Credits

This project is inspired by:

- https://github.com/DEFENDORe/pseudotv-plex
- https://github.com/vexorian/dizquetv

---

# License

This project is released under the **zlib license**.

See the [LICENSE](LICENSE) file for details.