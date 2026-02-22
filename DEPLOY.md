# 🚀 Decode AI Backend — Deployment Guide

## Step 1: Create GitHub Repository

1. Open your browser → go to: **https://github.com/new**
2. Sign in if asked
3. Fill in:
   - **Repository name:** `decode-ai-backend`
   - **Description:** `Decode AI backend proxy — secures Gemini API key`
   - **Visibility:** ✅ Public (required for Render free tier)
   - **Do NOT** check "Add README" or any other options
4. Click **"Create repository"**
5. Copy the repo URL shown (e.g. `https://github.com/YourName/decode-ai-backend.git`)

---

## Step 2: Push Code to GitHub

Open a terminal in the `backend/` folder and run:

```bash
git remote add origin https://github.com/YOUR_USERNAME/decode-ai-backend.git
git branch -M main
git push -u origin main
```

Replace `YOUR_USERNAME` with your actual GitHub username.

---

## Step 3: Deploy to Render.com

1. Go to: **https://render.com** → Sign in with GitHub
2. Click **"New +"** → **"Web Service"**
3. Click **"Connect a repository"** → select `decode-ai-backend`
4. Fill in settings:
   - **Name:** `decode-ai-backend`
   - **Region:** Singapore (closest to India)
   - **Branch:** `main`
   - **Build Command:** `npm install`
   - **Start Command:** `node server.js`
   - **Plan:** Free ✅
5. Scroll down to **"Environment Variables"** → click "Add Environment Variable":
   - Key: `GEMINI_API_KEY`
   - Value: `AIzaSyDplbyV_HxkemxxVdKKc1VFT88-6owtbwM`
6. Click **"Create Web Service"**
7. Wait ~2 minutes for it to deploy
8. You'll get a URL like: `https://decode-ai-backend.onrender.com`

---

## Step 4: Update the Extension

Once you have your Render URL, update ONE line in:
`extension/background.js`

Change:
```js
const BACKEND_URL = 'http://localhost:3000';
```
To:
```js
const BACKEND_URL = 'https://decode-ai-backend.onrender.com';
```

Then reload the extension in chrome://extensions/

---

## ✅ Test It

Visit: `https://decode-ai-backend.onrender.com/health`

You should see:
```json
{"status":"ok","service":"Decode AI Backend","version":"1.0.0"}
```
