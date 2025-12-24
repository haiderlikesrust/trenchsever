# Render Deployment Troubleshooting

## If Render Gets Stuck at Startup

### Problem
Render shows "Steady hands. Clean logs. Your app is almost live..." but never finishes.

### Solution 1: Health Check Endpoint ✅ (Already Added)

I've added a `/health` endpoint to your server. The `render.yaml` now points to it.

**What was added:**
- `GET /` - Returns server status
- `GET /health` - Health check endpoint
- Server listens on `0.0.0.0` (required for Render)

### Solution 2: Check Render Logs

1. Go to Render dashboard
2. Click on your service
3. Go to "Logs" tab
4. Look for errors or warnings

Common issues:
- ❌ Port binding errors
- ❌ Missing dependencies
- ❌ Server not starting

### Solution 3: Manual Health Check

1. Wait for service to show "Live" status
2. Visit: `https://your-service.onrender.com/health`
3. Should return: `{"status":"healthy"}`

### Solution 4: Update Render Settings

If still stuck:

1. Go to Render dashboard → Your service → Settings
2. **Health Check Path:** `/health`
3. **Start Command:** `node server.js`
4. **Build Command:** `npm install`
5. Click "Save Changes"
6. Manual Deploy → "Clear build cache & deploy"

### Solution 5: Check Server Logs

In Render logs, you should see:
```
🚀 Trench VC WebSocket server running on port 10000
🎤 Ready for connections!
✅ Health check available at http://0.0.0.0:10000/health
```

If you see errors, fix them.

### Solution 6: Free Tier Limitations

Render free tier:
- ⚠️ Services sleep after 15 min inactivity
- ⚠️ First request after sleep takes ~30 seconds (cold start)
- ⚠️ WebSocket support may be limited on free tier

**If WebSockets don't work on free tier:**
- Upgrade to paid plan ($7/month)
- Or use Railway (better free WebSocket support)

### Solution 7: Redeploy

1. In Render dashboard
2. Manual Deploy → "Clear build cache & deploy"
3. Wait for deployment to complete

### Quick Fix Checklist

- [x] Health check endpoint added (`/health`)
- [x] Server listens on `0.0.0.0`
- [x] `render.yaml` configured correctly
- [ ] Push updated code to GitHub
- [ ] Render auto-deploys or manual deploy
- [ ] Check logs for errors
- [ ] Test health endpoint

## After Server is Live

1. **Get your Render URL:**
   - Example: `trenchvc-websocket.onrender.com`

2. **Update frontend `client.js`:**
   ```javascript
   const wsServer = 'trenchvc-websocket.onrender.com';
   const protocol = 'wss:';
   const wsUrl = `${protocol}//${wsServer}`;
   ```

3. **Redeploy frontend (Vercel)**

4. **Test voice chat!** 🎤

