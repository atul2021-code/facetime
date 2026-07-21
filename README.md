# Ripple 📹

A free, open-source, peer-to-peer video calling app you can host yourself — no accounts, no backend server, no monthly fees. Built with WebRTC for crisp, low-latency video, and works globally between any two devices.

<p align="center">
  <img src="https://img.shields.io/badge/WebRTC-P2P-00A884" alt="WebRTC">
  <img src="https://img.shields.io/badge/dependencies-none%20(client--side)-25D366" alt="No backend">
  <img src="https://img.shields.io/badge/license-MIT-8696A0" alt="MIT License">
</p>

## Features

- 🌍 **Works from anywhere** — call across countries, networks, and firewalls
- 🎥 **Crisp video** — 720p @ 30fps by default, direct peer-to-peer streaming for low latency
- 🔑 **Room codes** — start a call, share a 6-character code, done. No sign-up, no login
- 🎙️ **Mute / camera toggle** — full in-call controls
- 📶 **Graceful fallback** — automatically degrades to audio-only, video-only, or viewer mode if a device is missing
- 💸 **100% free infrastructure** — public STUN/TURN relays and a free signaling broker, no paid services required
- 📱 **Responsive** — works on desktop and mobile browsers

## How it works

Ripple is a **single static HTML file** — there's no server to run or database to manage.

- **Media streaming**: [WebRTC](https://webrtc.org/) sends video/audio directly between the two callers' browsers (peer-to-peer), keeping latency low.
- **Connecting two people ("signaling")**: [PeerJS](https://peerjs.com/) and its free public cloud broker handle exchanging the technical handshake needed to establish a call.
- **Getting through firewalls/NATs**: free public [Google STUN](https://stackoverflow.com/questions/26356124) servers plus the [Open Relay Project](https://www.metered.ca/tools/openrelay/)'s free TURN relay servers, so calls still connect even on strict corporate or mobile networks.

## Getting started

### 1. Host the file

Since it's just one HTML file, any static hosting works — for example:

**Netlify Drop (fastest, no account)**
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag `video-call.html` into the browser
3. You'll get a live URL instantly

**GitHub Pages**
```bash
git add video-call.html
git commit -m "Add Ripple video calling app"
git push
```
Then enable **Settings → Pages** on your repo and point it at the branch.

**Vercel**
```bash
npx vercel video-call.html
```

### 2. Make a call

1. Open the hosted link and click **Create a room** — you'll get a 6-character code
2. Share that code with the other person (any messaging app works)
3. They open the same link, click **Join a call**, and enter the code
4. Both allow camera/microphone access — the call connects automatically

Both people must open the **same hosted URL** — after that, distance and network type don't matter.

## Project structure

```
video-call.html   # everything — UI, styling, and calling logic in one file
```

## Tech stack

| Purpose | Tool | Cost |
|---|---|---|
| Video/audio streaming | WebRTC (browser native) | Free |
| Call signaling | PeerJS + public cloud broker | Free |
| NAT traversal (STUN) | Google public STUN servers | Free |
| NAT traversal (TURN relay) | Open Relay Project | Free |

## Known limitations

- The free TURN relay has shared, limited bandwidth — fine for personal use, but not built for heavy simultaneous traffic. For guaranteed reliability at scale, swap in a paid TURN provider (e.g. Twilio, Metered.ca paid tier) by editing the `ICE_SERVERS` config in the script.
- Calls are 1-to-1 only; group calling isn't implemented.
- No call history or persistence — it's fully in-memory per session, by design (privacy-friendly, zero backend).

## Roadmap ideas

- [ ] Group calls (3+ participants)
- [ ] In-call text chat
- [ ] Screen sharing
- [ ] Call recording

## License

MIT — use it, modify it, host it however you like.
