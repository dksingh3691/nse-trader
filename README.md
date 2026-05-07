# NSE Paper Trader — PWA Deployment Guide

## Files in this package
```
index.html     ← The complete app (React + all logic)
sw.js          ← Service Worker (offline support)
manifest.json  ← PWA manifest (install on Android)
icon-192.png   ← App icon (home screen)
icon-512.png   ← App icon (splash screen)
README.md      ← This guide
```

---

## METHOD 1 — Netlify (Fastest, Recommended — Free)

1. Go to https://netlify.com → Sign Up (free)
2. Click **"Add new site" → "Deploy manually"**
3. **Drag and drop the entire folder** (all 5 files) onto the upload area
4. Netlify gives you a URL like: `https://nse-trader-abc123.netlify.app`
5. Open that URL on your Android phone in Chrome
6. Chrome shows **"Add to Home screen"** banner at bottom → Tap it
7. App installs with icon, runs fullscreen like a native app ✓

---

## METHOD 2 — GitHub Pages (Also Free)

1. Go to https://github.com → Create account → New repository
2. Name it `nse-trader`, set to **Public**
3. Upload all 5 files (drag & drop in browser)
4. Go to Settings → Pages → Source: **main branch / root**
5. Your URL: `https://yourusername.github.io/nse-trader`
6. Open on Android Chrome → Add to Home Screen

---

## METHOD 3 — Run Locally (No Internet Hosting)

If you have Python installed on your PC:
```bash
cd nse-pwa
python3 -m http.server 8080
```
Then on your phone (same WiFi):
- Open Chrome → `http://YOUR_PC_IP:8080`
- Add to Home Screen

---

## Installing on Android

Once you open the hosted URL in **Chrome on Android**:

1. Chrome shows a banner: **"Add NSE Paper Trader to Home Screen"** — tap it
2. OR tap Chrome menu (⋮) → **"Add to Home screen"** → **"Install"**
3. The app appears on your home screen with the ₹ chart icon
4. Tap it — it opens fullscreen, no browser bar, like a real app

### What makes it feel native:
- ✅ Full screen (no browser chrome)
- ✅ Works offline (cached via Service Worker)
- ✅ Data persists via localStorage (survives restarts)
- ✅ Live NSE/BSE prices via Yahoo Finance (when online)
- ✅ Home screen icon + splash screen
- ✅ Back button works normally

---

## Updating the App Later

Just re-upload the new `index.html` to Netlify/GitHub.
The Service Worker auto-updates on next open.

---

## Troubleshooting

| Issue | Fix |
|---|---|
| "Add to Home Screen" not showing | Must be on HTTPS (Netlify/GitHub auto-provides this) |
| Prices not loading | Yahoo Finance may block during market hours — tap ↻ refresh |
| App looks small on phone | Pinch-zoom disabled by design; use landscape for table view |
| Data disappeared | localStorage was cleared — re-add your groups |
