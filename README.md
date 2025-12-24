# Trench VC - WebSocket Server

This is the WebSocket signaling server for Trench VC voice chat.

## What This Does

- Handles WebSocket connections for WebRTC signaling
- Connects users together for peer-to-peer voice chat
- Manages client IDs and message relaying

## Local Development

1. Install dependencies:
```bash
npm install
```

2. Start the server:
```bash
npm start
```

Server will run on `http://localhost:3000`

## Deployment

### Railway (Recommended)

1. Go to [railway.app](https://railway.app)
2. New Project → Deploy from GitHub
3. Connect this folder/repo
4. Set Start Command: `node server.js`
5. Railway auto-detects Node.js and installs dependencies

### Render

1. Go to [render.com](https://render.com)
2. New → Web Service
3. Connect GitHub repo
4. Build Command: `npm install`
5. Start Command: `node server.js`

## Environment Variables

- `PORT` - Server port (default: 3000, Railway/Render sets this automatically)

## After Deployment

1. Get your deployment URL (e.g., `trenchvc.railway.app`)
2. Update the frontend `client.js` file:
   ```javascript
   const wsServer = 'trenchvc.railway.app';
   const protocol = 'wss:';
   const wsUrl = `${protocol}//${wsServer}`;
   ```

## Files

- `server.js` - Main WebSocket server
- `package.json` - Dependencies

That's it! Simple and clean. 🚀

