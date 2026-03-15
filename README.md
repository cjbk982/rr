# Rune Raider — PWA Deployment Guide

## What's Included

```
rune-raider-pwa/
├── index.html          ← The complete game (HTML + CSS + JS, all-in-one)
├── manifest.json       ← PWA manifest for app installation
├── sw.js               ← Service worker for offline play
├── favicon.ico         ← Browser favicon
├── icon-16.png         ← 16×16 icon
├── icon-32.png         ← 32×32 icon
├── icon-48.png         ← 48×48 icon
├── icon-72.png         ← 72×72 icon
├── icon-96.png         ← 96×96 icon
├── icon-128.png        ← 128×128 icon
├── icon-144.png        ← 144×144 icon (Windows tile)
├── icon-152.png        ← 152×152 icon (Apple Touch)
├── icon-192.png        ← 192×192 icon (Android)
├── icon-384.png        ← 384×384 icon
├── icon-512.png        ← 512×512 icon (splash/store)
├── splash-*.png        ← Apple splash screens (5 sizes)
└── README.md           ← This file
```

## How to Deploy

### Option 1: GitHub Pages (Free, Easiest)

1. Create a new GitHub repository (e.g., `rune-raider`)
2. Upload all files from this folder to the repository root
3. Go to **Settings → Pages → Source** → select `main` branch
4. Your game will be live at `https://yourusername.github.io/rune-raider/`
5. Open that URL on your phone → browser will prompt "Add to Home Screen"

### Option 2: Netlify (Free, Drag & Drop)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag the entire `rune-raider-pwa` folder onto the page
3. Done! Netlify gives you a URL instantly
4. Optionally set a custom domain in site settings

### Option 3: Vercel (Free)

1. Install Vercel CLI: `npm i -g vercel`
2. Run `vercel` in this folder
3. Follow the prompts — deployed in seconds

### Option 4: Any Static Host

Upload all files to any web server or static hosting (Firebase Hosting,
Cloudflare Pages, AWS S3 + CloudFront, etc). The only requirement is
**HTTPS** — service workers require a secure connection.

## Installing as an App

### Android (Chrome)
- Visit the deployed URL in Chrome
- An "Install" banner should appear automatically
- Or tap the ⋮ menu → "Install app" / "Add to Home Screen"
- The game appears as a standalone app on your home screen

### iOS (Safari)
- Visit the deployed URL in Safari
- Tap the Share button (□↑)
- Tap "Add to Home Screen"
- The game launches fullscreen like a native app
- Note: iOS uses the apple-touch-icon and splash screens included

### Desktop (Chrome/Edge)
- Visit the URL in Chrome or Edge
- Click the install icon (⊕) in the address bar
- Or use Menu → "Install Rune Raider..."
- Opens as a standalone desktop window

## Features

- **8 progressive levels** with increasing difficulty
- **Retro pixel art** rendered in real-time on canvas
- **Sound effects** via Web Audio API (no audio files needed)
- **Touch controls** auto-appear on mobile/touch devices
- **Keyboard controls** for desktop play
- **Offline support** — plays without internet once cached
- **High score** saved in localStorage
- **Pause/resume** — P key or pause button
- **Screen shake** and particle effects
- **Responsive** — scales to any screen size

## Controls

| Action     | Keyboard       | Mobile          |
|------------|---------------|-----------------|
| Move       | Arrow keys / WASD | D-pad        |
| Climb      | Up/Down        | D-pad Up/Down   |
| Dig Left   | Z or Q         | DIG ◀ button    |
| Dig Right  | X or E         | DIG ▶ button    |
| Pause      | P or Escape    | Pause button    |

## Customization

The game is entirely self-contained in `index.html`. To customize:

- **Colors**: Edit the `PAL` object in the JavaScript section
- **Levels**: Edit the `LEVELS` array — each level is a 26×16 character grid
- **Level tiles**: `B`=brick, `G`=gold brick (diggable), `H`=ladder,
  `~`=rope, `4`=gem, `5`=player start, `6`=enemy, `7`=exit, `^`=spike,
  `.`=empty
- **Speed/physics**: Adjust constants in `updatePlayer()` and `updateEnemies()`
- **Sound**: Modify frequencies in the `Audio` object

## Tech Stack

- Pure HTML5 / CSS3 / Vanilla JavaScript
- Canvas 2D for rendering
- Web Audio API for sound
- Service Worker for offline caching
- Web App Manifest for installation
