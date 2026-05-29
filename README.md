# Chat Overlay

A free, minimal Twitch chat overlay for OBS and Streamlabs. Clean, fast, fully configurable — no watermarks, no subscriptions, no third-party tools required.

<img width="399" height="192" alt="image" src="https://github.com/user-attachments/assets/8bd60567-5b26-4e33-81e4-4f90bee4c983" />


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
- **Live settings panel** — press `` ` `` anytime while the widget is running to adjust anything without reloading
- **OBS-safe** — uses `localStorage`, no `history.replaceState` errors
- **No external network requests** — all fonts are system fonts

---

## How it works

1. Open the page — the **setup UI** always loads first
2. Configure your channel, style, and options
3. Click **Launch Widget →** — setup disappears and the overlay goes live
4. Press `` ` `` at any time to open the **live settings panel** and adjust things on the fly
5. From the live panel, click **Back to Setup** to return to the full setup UI

Your settings are saved to `localStorage` automatically so they're pre-filled next time you open the page.

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

Open the page in your browser. The setup UI will be visible. Fill in:

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

The setup page will show briefly when OBS loads — click **Launch Widget →** to start the overlay.

---

## Badges (optional)

Badges require Twitch OAuth. The widget handles this automatically — no token pasting required:

1. Go to [dev.twitch.tv/console/apps](https://dev.twitch.tv/console/apps) and create a free app
2. Set the OAuth redirect URI to your widget's URL (your GitHub Pages URL, or `http://localhost` for local use)
3. Paste your Client ID into the setup UI
4. Click **Connect Twitch** — you'll be redirected to Twitch to approve
5. After approving, you'll land back on the setup page with badges enabled

The token is stored silently in `localStorage` — you'll never see or handle a token string.

If you skip this, the widget still works perfectly — it just won't show badges.

---

## Live Settings Panel

Press `` ` `` (backtick) while the widget is running to open the settings panel. Changes apply instantly.

**What you can change:**
- Font size and name size
- Font family and message style
- Text color, bubble color, opacity
- Message gap, padding, max messages
- Direction (bottom-up / top-down) and fade mode
- Timestamps, badges, emotes, hide `!` commands

**Controls:**
- **Save & Apply** — writes to `localStorage` so changes persist on OBS reload
- **Clear Chat** — wipes all visible messages instantly
- **Back to Setup** — kills the connection and returns to the full setup UI
- **Keybind** — click the key box and press any key to change the panel toggle shortcut

---

## Message styles

| Style | Description |
|---|---|
| **Bubble** | Rounded background behind each message |
| **Pill** | Fully rounded pill-shaped background |
| **Bar** | Flat background with a colored left border matching the username color |
| **Minimal** | No background — text only |
| **Outline** | Subtle border, no background fill |
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
