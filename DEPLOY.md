# Deploying laureneanthony.com for free on GitHub Pages

This folder is a complete, ready-to-host static site: `index.html` (About), `cv.html` (CV), `contact.html`, `style.css`, and an `assets/` folder with your CV PDF and images. Total cost going forward: just your existing domain renewal (~$12-20/yr, whatever you already pay your registrar) — hosting itself is $0.

## 1. Add your photo (optional)
`assets/profile.jpg` and `assets/kandinsky.png` weren't downloadable from this sandbox (Squarespace's image CDN isn't reachable here). Before you take the Squarespace site down:
1. Open your Squarespace site, right-click your headshot → "Save image as" → save it as `profile.jpg`
2. Do the same for the Kandinsky detail image on your Contact page → save as `kandinsky.png`
3. Drop both files into the `assets/` folder, replacing nothing (they don't exist yet) — the pages will pick them up automatically. If you skip this, the photo areas just won't show; nothing breaks.

## 2. Create a GitHub account and repository
1. Go to github.com and sign up (free).
2. Click "New repository." Name it anything, e.g. `laureneanthony-site`. Keep it Public. Don't initialize with a README (you already have one here).
3. On the new repo's Quick Setup page, follow the "…or push an existing repository" instructions, OR simply drag-and-drop all the files in this folder into GitHub's web UI ("Add file" → "Upload files") — no command line needed.

## 3. Enable GitHub Pages
1. In the repo, go to Settings → Pages.
2. Under "Build and deployment," set Source to "Deploy from a branch," Branch to `main`, folder `/ (root)`. Save.
3. GitHub will give you a URL like `https://yourusername.github.io/laureneanthony-site/` within a minute or two — confirm the site loads there first.

## 4. Point your domain at GitHub Pages
The `CNAME` file in this folder already tells GitHub to serve this site at `laureneanthony.com`. You still need to update DNS at wherever you registered the domain (GoDaddy, Namecheap, Google Domains, or Squarespace Domains if it's registered through Squarespace itself):

Add these DNS records:
- **A records** for the root domain (`laureneanthony.com`), pointing to GitHub's IPs:
  - 185.199.108.153
  - 185.199.109.153
  - 185.199.110.153
  - 185.199.111.153
- **CNAME record** for `www` pointing to `yourusername.github.io`

Then in GitHub, Settings → Pages → Custom domain, enter `laureneanthony.com`, save, and check "Enforce HTTPS" once it's available (may take a few hours for the SSL certificate to provision).

DNS changes can take anywhere from a few minutes to 24 hours to propagate.

## 5. Cancel Squarespace
Once `laureneanthony.com` is loading the new site correctly (test on a few devices/networks), cancel your Squarespace subscription. Make sure your domain itself isn't registered *through* Squarespace — if it is, you'll need to transfer it to an external registrar (e.g., Cloudflare Registrar or Namecheap, both cheap/at-cost) before closing the account, or your domain could go down with it.

## Updating the site later
Just edit the HTML files directly (they're plain text) and re-upload/push to GitHub — changes go live within a minute or two. No build step required.
