# Chat Overlay

A free, minimal Twitch chat overlay for OBS and Streamlabs. Clean, fast, fully configurable — no watermarks, no subscriptions, no third-party tools required.

![Chat Overlay Preview](preview.png)

---

## Features

- **Live Twitch chat** via IRC WebSocket — no API key needed for basic use
- **6 message styles** — Bubble, Pill, Bar, Minimal, Outline, Compact
- **6 font options** — all system fonts, no external requests
- **Full color control** — text color, bubble color, opacity
- **Configurable typography** — font size, name size, gap, padding
- **Message direction** — bottom-up or top-down
- **Fade modes** — push off (oldest disappears when list fills) or timed fade after N seconds
- **Toggles** — timestamps, badges, emotes, hide `!` commands
- **Live settings panel** — press `` ` `` while the widget is running to adjust anything without reloading
- **OBS-safe** — uses `localStorage`, no `history.replaceState` errors
- **No external network requests** — all fonts are system fonts

---

## Setup

### 1. Host it

**Option A — GitHub Pages (recommended)**
1. Fork this repo
2. Go to Settings → Pages → Source: `main` branch, `/ (root)`
3. Your widget will be live at `https://yourusername.github.io/Chat-Overlay`

**Option B — Local file**
Open `index.html` directly in a browser. Works fine for personal use.

---

### 2. Configure

Open the page in your browser. You'll see the setup UI:

| Section | What to fill in |
|---|---|
| **Channel name** | Your Twitch channel (required) |
| **Client ID** | Your Twitch app Client ID — only needed if you want badges |
| **Connect Twitch** | Logs in via OAuth to enable badge display |
| **Style preset** | Pick the message bubble style |
| **Font** | Pick from 6 system fonts |
| **Colors** | Text color, bubble background, opacity |
| **Typography** | Font sizes, gap between messages, padding |
| **Behaviour** | Direction, fade mode, max messages, toggles |
| **Widget size** | Match your OBS canvas size |

Click **Launch Widget →** when done.

---

### 3. Add to OBS

1. Add a new **Browser Source** in OBS
2. Check **Local file** if hosting locally, or paste your GitHub Pages URL
3. Set Width and Height to match what you entered in setup
4. Check **Shutdown source when not visible** and **Refresh browser when scene becomes active**
5. Click OK

Your config saves to `localStorage` automatically — the widget reconnects and restores your settings every time OBS loads it.

---

## Badges (optional)

Badges require a Twitch OAuth token. The widget handles this automatically:

1. Go to [dev.twitch.tv/console/apps](https://dev.twitch.tv/console/apps) and create a free app
2. Set the OAuth redirect URI to your widget's URL (GitHub Pages URL or `http://localhost` for local use)
3. Copy your Client ID and paste it into the setup UI
4. Click **Connect Twitch** — you'll be redirected to Twitch to log in
5. After approving, you'll be redirected back and badges will be enabled

The token is stored silently in `localStorage` — you'll never see or paste a token string.

If you skip this step, the widget still works perfectly — it just won't show badges.

---

## Live Settings Panel

Press `` ` `` (backtick) while the widget is running to open a settings panel without reloading OBS.

**What you can change live:**
- Font size and name size
- Font family and message style
- Text color, bubble color, opacity
- Message gap, padding, max messages
- Direction and fade mode
- Timestamps, badges, emotes, hide commands

**Other controls:**
- **Save & Apply** — writes changes to `localStorage` so they persist on reload
- **Clear Chat** — wipes all messages from screen instantly
- **Back to Setup** — returns to the full setup UI
- **Keybind** — click the key box and press any key to change the toggle shortcut

---

## Message styles

| Style | Description |
|---|---|
| **Bubble** | Rounded background behind each message |
| **Pill** | Fully rounded pill-shaped background |
| **Bar** | Flat background with a colored left border matching the username color |
| **Minimal** | No background — text only |
| **Outline** | No background but a subtle white border |
| **Compact** | Tighter padding, denser layout |

---

## Browser / OBS compatibility

| Environment | Status |
|---|---|
| OBS Browser Source | ✅ Fully supported |
| Streamlabs Browser Source | ✅ Fully supported |
| Chrome / Edge / Firefox | ✅ Fully supported |
| Local file (file://) | ✅ Works |

---

## License

MIT — free to use, modify, and redistribute. Credit appreciated but not required.
