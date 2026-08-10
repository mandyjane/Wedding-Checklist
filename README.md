# Wedding Checklist PWA

A progressive web app for tracking wedding planning — works offline, installs like a native app, and syncs data to GitHub.

## Quick Setup

### 1. Create the GitHub repo and enable Pages

```bash
# Create a new repo on GitHub called wedding-checklist
# It needs to be PUBLIC for GitHub Pages (free tier)
# Then clone it and copy these files in:
git clone https://github.com/YOUR_USERNAME/wedding-checklist.git
cd wedding-checklist
# Copy all files from this folder into the repo
git add .
git commit -m "Initial commit"
git push
```

Then on GitHub:

1. Go to your repo → **Settings → Pages**
2. Under "Source", select **Deploy from a branch**
3. Branch: **main**, folder: **/ (root)**
4. Click **Save**
5. Your site will be live at `https://YOUR_USERNAME.github.io/wedding-checklist/`

### 2. Create a personal access token

Your checklist data saves as `data/checklist.json` in the same repo. You need a token so the app can write to it.

1. Go to **GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens**
2. Click **Generate new token**
3. Give it a name like "Wedding Checklist"
4. Set expiry to a custom date after your wedding
5. Under **Repository access**, select **Only select repositories** → choose `wedding-checklist`
6. Under **Permissions → Repository permissions**, set **Contents** to **Read and write**
7. Generate the token and copy it

### 3. Install on your phone

1. Open `https://YOUR_USERNAME.github.io/wedding-checklist/` in Safari (iOS) or Chrome (Android)
2. **iOS**: Tap the Share button → **Add to Home Screen**
3. **Android**: Tap the menu → **Add to Home Screen** or **Install app**
4. Open the app from your home screen
5. Tap **⚙ Connect GitHub**
6. Your repo and file path are pre-filled — just paste your token
7. Tap **Save & Sync**

## How it works

- **Offline first**: The app works without internet. Data saves to your phone's local storage instantly.
- **GitHub sync**: Every change also saves to `data/checklist.json` in this repo.
- **Tap ↻ Sync** to pull the latest from GitHub (useful if you use it on multiple devices).
- **Dark mode**: Automatically follows your phone's light/dark setting.
- The `data/` folder is excluded from the service worker cache, so your data always syncs fresh.

## Files

```
index.html          — The entire app (single file, no build step)
manifest.json       — PWA manifest for home screen install
sw.js               — Service worker for offline caching
icons/              — App icons (192px and 512px)
data/checklist.json — Your checklist data (created automatically on first sync)
```
