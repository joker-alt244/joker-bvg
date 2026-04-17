# Bug-Web (BAHIRAVA BUG WEB)

## Project Overview
A Node.js/Express web application that connects to WhatsApp via the Baileys library and provides a dashboard for sending various message payloads to targets.

## Tech Stack
- **Backend**: Node.js + Express.js
- **WhatsApp**: @whiskeysockets/baileys (via github:DGXeon13/dgxeon-soket)
- **Logging**: @sabir7718/log, pino
- **Cache**: node-cache
- **Frontend**: Vanilla HTML/CSS/JS (public/ folder)

## Project Structure
```
index.js          - Main Express server + WhatsApp session management
package.json      - Dependencies
Procfile          - Heroku deployment config
.npmrc            - npm config (legacy-peer-deps=true for jimp version conflict)
.gitignore        - Git ignore (node_modules, Love/ sessions)
public/           - Frontend HTML files (login.html, dashboard.html)
SY/S7/            - Attack logic modules
  gcFrz.js        - Group freeze logic
  StickerCrash.js - Sticker crash logic
  killsystem.js   - Kill system logic
  IosInvisible.js - iOS invisible logic
  Xdelay.js       - X delay logic
  Xgc.js          - X group crash logic
Love/             - WhatsApp session storage (gitignored)
```

## Port Configuration
- Development (Replit): PORT 5000 (default)
- Production (Heroku): uses `process.env.PORT` dynamically

## Heroku Deployment
- `Procfile`: `web: node index.js`
- `.npmrc`: `legacy-peer-deps=true` (required due to jimp peer dependency conflict)
- `engines` in package.json: Node >= 20.0.0

## Key Notes
- Sessions stored in `Love/` directory (ephemeral on Heroku - will reset on dyno restart)
- App uses `process.env.PORT || 5000` for flexible port binding
- npm install requires `--legacy-peer-deps` due to jimp version conflict between root and baileys
