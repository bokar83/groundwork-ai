# Deploy Guide — Groundwork AI

Two deployment targets: Replit (hackathon / demo) and Hostinger static hosting (production).

---

## Option A: Replit (fastest — hackathon / demo)

### Method 1: GitHub import (recommended)

1. Push this repo to GitHub (e.g. `bokar83/clarity-ai`)
2. Go to [replit.com](https://replit.com) → **+ Create Repl**
3. Choose **Import from GitHub**
4. Paste the repo URL → click **Import from GitHub**
5. Replit detects `index.html` and sets up a static site automatically
6. Click **Run** — your app is live at `https://<repl-name>.<username>.repl.co`

### Method 2: Drag and drop

1. Go to [replit.com](https://replit.com) → **+ Create Repl**
2. Choose template: **HTML, CSS, JS**
3. Delete the default `index.html`
4. Drag your `index.html` file into the Replit file pane
5. Click **Run**

### Method 3: Replit AI Agent (rebuild from spec)

1. Create a new **HTML, CSS, JS** Repl
2. Open Replit AI Agent (the chat panel)
3. Paste the full contents of `replit-kickoff-prompt.md`
4. Agent builds the complete `index.html` on the first pass

### Custom domain on Replit

Replit free tier gives a `.repl.co` URL. For a custom domain:
- Upgrade to Replit Core ($20/mo) → **Deployments** tab → **Custom domain**
- Point your domain's CNAME to `<repl-name>.<username>.repl.co`

---

## Option B: Hostinger Static Hosting (production)

### Prerequisites

- Hostinger account with a hosting plan (any plan works — this is a static file)
- Access to Hostinger hPanel or File Manager

### Method 1: File Manager upload

1. Log in to [hpanel.hostinger.com](https://hpanel.hostinger.com)
2. Go to **File Manager** → navigate to `public_html/` (or the subdirectory you want)
3. Upload `index.html`
4. If deploying to a subdirectory (e.g. `/audit/`): create folder `audit/`, upload `index.html` inside it
5. Visit `https://yourdomain.com/audit/` — the app is live

### Method 2: FTP / SFTP

```bash
# Using sftp (replace with your Hostinger credentials)
sftp username@yourdomain.com
cd public_html
# or cd public_html/audit if using a subfolder
put index.html
exit
```

Hostinger FTP credentials: hPanel → **FTP Accounts** section.

### Method 3: Via agentsHQ deploy script

The agentsHQ `hosting_deployStaticWebsite` tool handles Hostinger deploys.
Use this path only from within a Claude Code session with VPS access.

**Important:** Deploying to a directory on Hostinger WIPES the existing files in that directory.
Always deploy the full file set, not just updated files, to avoid partial-wipe.

### Subdirectory vs root deploy

| Target URL | Upload to |
|---|---|
| `yourdomain.com` | `public_html/index.html` |
| `yourdomain.com/audit` | `public_html/audit/index.html` |
| `audit.yourdomain.com` | Create subdomain in hPanel → upload to its `public_html/` |

---

## Post-deploy checklist

- [ ] Open the live URL and complete a full audit flow end to end
- [ ] Test on mobile (iOS Safari + Android Chrome)
- [ ] Confirm "Download Report (PDF)" opens the browser print dialog
- [ ] Confirm "Book a Free Strategy Call" button links to the correct Calendly URL
- [ ] Confirm Chart.js radar chart renders (requires internet — CDN dependency)
- [ ] Update the Calendly link from `https://calendly.com/boubacarbarry` to your live link if different
