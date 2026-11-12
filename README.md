# PENNYWISE — Personal Finance Workspace (PWA)

A private, **local-first** personal finance web app.  
All data (transactions, budgets, goals, bills, settings) is stored in the browser’s **localStorage** on the user’s device. Nothing is sent to a server.

## Features

- Dashboard with income / expenses / balance overview  
- Record Manager (add, edit, filter transactions)  
- Financial Ledger (spreadsheet-style views + CSV export)  
- Charts & visualizations  
- Budget Organizer  
- Savings Goals  
- Expense Detective (rule-based insights)  
- Purchase Planner  
- Reports & full JSON backup / restore  
- Dark / Light theme, multi-currency  
- **Installable Progressive Web App** (works offline after first visit)

## Files

| File | Purpose |
|------|---------|
| `index.html` | Main app (single-page) |
| `manifest.json` | PWA manifest (name, icons, theme) |
| `sw.js` | Service worker (caches app shell for offline use) |
| `icons/` | App icons (72–512 px + maskable) |

## How data is saved

- Everything is written to `localStorage` under the key `pennywise_data_v1`.
- Changes are saved automatically when you add/edit/delete records, change settings, etc.
- Data stays on the device. Clearing browser data or using a different browser/profile will show an empty app.
- Use **Reports → Export full JSON backup** to keep a safe copy.

## Run locally

Any static server works. Examples:

```bash
# Python
python3 -m http.server 8080

# Node (if you have npx)
npx serve .
```

Then open `http://localhost:8080`.

> Service workers and “Add to Home Screen” require HTTPS (or localhost).

## Publish on GitHub + free hosting

### 1. Create a GitHub repository

1. Go to [github.com/new](https://github.com/new).
2. Repository name example: `pennywise` or `pennywise-pwa`.
3. Public (required for free GitHub Pages).
4. **Do not** initialize with README if you already have these files.
5. Create repository.

### 2. Push these files

On your computer:

```bash
# In the folder that contains index.html, manifest.json, sw.js, icons/
git init
git add .
git commit -m "Initial PENNYWISE PWA"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

Replace `YOUR_USERNAME` and `YOUR_REPO` with your values.

### 3. Enable GitHub Pages

1. Open the repository on GitHub.
2. **Settings** → **Pages** (left sidebar).
3. Under **Source**, choose **Deploy from a branch**.
4. Branch: `main`, folder: `/ (root)`.
5. Save.
6. After a minute, your app will be live at:

   `https://YOUR_USERNAME.github.io/YOUR_REPO/`

### 4. Install as an app

- **Desktop (Chrome/Edge)**: open the live URL → address bar install icon (or menu → “Install PENNYWISE”).
- **Android**: open in Chrome → menu → “Install app” / “Add to Home screen”.
- **iOS**: open in Safari → Share → “Add to Home Screen”.

After install, the app opens full-screen and works offline (the shell is cached; your financial data is still only in localStorage on that device).

## Optional: custom domain

In the same Pages settings you can add a custom domain and follow GitHub’s DNS instructions.

## Privacy note

PENNYWISE never talks to a backend. Your records never leave the browser unless you export a backup file yourself.
