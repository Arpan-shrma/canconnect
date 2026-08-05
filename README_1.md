# Toronto Gentrification Explorer — Project Page

A static showcase page for the [Toronto Gentrification Explorer](https://arpan-shrma.shinyapps.io/toronto_gentrification_app/),
an R Shiny dashboard forecasting gentrification risk across Toronto's 25 wards (2023–2028).

This repo hosts **only the landing page** (`index.html`) — the actual interactive app lives
on shinyapps.io, since GitHub Pages can only serve static files and can't run a live R Shiny
server.

## Deploy this as a GitHub Pages site (5 minutes)

1. **Create a new repo** on GitHub — e.g. `toronto-gentrification-explorer`.
   - Go to github.com → **New repository**
   - Name it, set it to **Public**, don't initialize with a README (you already have one)

2. **Upload the files**
   - On the repo page, click **Add file → Upload files**
   - Drag in `index.html` and `README.md` from this folder
   - Commit directly to `main`

3. **Turn on GitHub Pages**
   - Go to the repo's **Settings → Pages**
   - Under "Build and deployment" → Source, select **Deploy from a branch**
   - Branch: `main`, folder: `/ (root)` → **Save**

4. **Wait ~1 minute**, then your page will be live at:
   `https://arpan-shrma.github.io/toronto-gentrification-explorer/`
   (GitHub shows you the exact URL at the top of the Pages settings once it's built)

## Alternative: command line

```bash
git init
git add index.html README.md
git commit -m "Add project showcase page"
git branch -M main
git remote add origin https://github.com/arpan-shrma/toronto-gentrification-explorer.git
git push -u origin main
```

Then enable Pages the same way as step 3 above.

## After it's live

- Add the GitHub Pages URL to your resume/LinkedIn alongside the shinyapps.io link
- Consider adding 1–2 screenshots or a short screen-recording GIF of the live app into
  this repo and linking them from `index.html` for people who can't access shinyapps.io
  right away (free-tier apps sleep after inactivity and take a few seconds to wake up)
