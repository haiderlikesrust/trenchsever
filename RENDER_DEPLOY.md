# Deploying to Render with render.yaml

## Quick Deploy (Easiest Method)

1. **Push your code to GitHub:**
   ```bash
   cd C:\Users\Gamer\Desktop\trenchvc-server
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin YOUR_GITHUB_REPO_URL
   git push -u origin main
   ```

2. **Go to Render:**
   - Visit [render.com](https://render.com)
   - Sign up/Login (free account)

3. **Create Blueprint:**
   - Click "New" → "Blueprint"
   - Connect your GitHub account
   - Select your repository (`trenchvc-server`)
   - Render will automatically detect `render.yaml`
   - Click "Apply"

4. **Done!** 🎉
   - Render will deploy automatically
   - You'll get a URL like: `trenchvc-websocket.onrender.com`
   - Copy this URL for your frontend

## What render.yaml Does

The `render.yaml` file automatically configures:
- ✅ Service type: Web service
- ✅ Environment: Node.js
- ✅ Plan: Free tier
- ✅ Build command: `npm install`
- ✅ Start command: `node server.js`
- ✅ Environment variables
- ✅ Auto-deploy on git push

## After Deployment

1. **Get your Render URL:**
   - Go to Render dashboard
   - Click on your service
   - Copy the URL (e.g., `trenchvc-websocket.onrender.com`)

2. **Update Frontend:**
   - Edit `client.js` in your main project
   - Update WebSocket URL:
   ```javascript
   const wsServer = 'trenchvc-websocket.onrender.com';
   const protocol = 'wss:';
   const wsUrl = `${protocol}//${wsServer}`;
   ```

3. **Redeploy Frontend (Vercel):**
   - Push changes to trigger Vercel redeploy
   - Voice chat will work! 🎤

## Render Free Tier Limits

- ✅ 750 hours/month free
- ✅ Auto-sleeps after 15 min inactivity (wakes on request)
- ✅ WebSocket support (on paid plans, free may have limitations)
- ⚠️ First request after sleep takes ~30 seconds (cold start)

## Troubleshooting

**Service won't start:**
- Check Render logs
- Verify `package.json` has all dependencies
- Ensure `server.js` is in root directory

**WebSocket not connecting:**
- Free tier may have WebSocket limitations
- Consider upgrading to paid plan ($7/month)
- Or use Railway (better free WebSocket support)

**Slow first connection:**
- Normal on free tier (cold start)
- Subsequent connections are fast

## Alternative: Railway

If Render free tier has WebSocket issues:
- Railway has better free WebSocket support
- Same deployment process
- No render.yaml needed (just deploy)

