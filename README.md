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

### Render (Recommended - Has render.yaml)

**Option 1: Using render.yaml (Easiest)**
1. Go to [render.com](https://render.com)
2. New → Blueprint
3. Connect your GitHub repository
4. Render will auto-detect `render.yaml` and configure everything
5. Click "Apply" - Done! 🎉

**Option 2: Manual Setup**
1. Go to [render.com](https://render.com)
2. New → Web Service
3. Connect GitHub repo
4. Render will use `render.yaml` automatically
5. Or manually set:
   - Build Command: `npm install`
   - Start Command: `node server.js`

### Railway

1. Go to [railway.app](https://railway.app)
2. New Project → Deploy from GitHub
3. Connect this folder/repo
4. Set Start Command: `node server.js`
5. Railway auto-detects Node.js and installs dependencies

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

