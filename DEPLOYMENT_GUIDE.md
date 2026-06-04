# GitHub Pages Deployment Guide

## Step-by-Step: Upload to GitHub and Get a Shareable Link

---

### OPTION A: Using GitHub Web Interface (No Git Required)

This is the easiest method — everything is done in the browser.

#### Step 1: Create a GitHub Account (if you don't have one)

1. Go to **https://github.com**
2. Click **Sign up** and complete registration
3. Verify your email address

#### Step 2: Create a New Repository

1. Once logged in, click the **+** icon (top-right) → **New repository**
2. Fill in:
   - **Repository name**: `aes-utilization-report`
   - **Description**: `AES Oracle Resource Utilization Report`
   - **Visibility**: Choose **Private** (recommended for confidential data) or **Public**
   - Check **Add a README file**
3. Click **Create repository**

#### Step 3: Upload the Files

1. In your new repository, click **Add file** → **Upload files**
2. Drag and drop ALL files from the package folder:
   - `index.html` (the main dashboard)
   - `README.md` (documentation)
   - `.nojekyll` (required for GitHub Pages)
3. In the commit message box, type: `Initial upload - AES Resource Utilization Report`
4. Click **Commit changes**

> **Important**: Make sure `index.html` is in the ROOT of the repository, not inside a subfolder.

#### Step 4: Enable GitHub Pages

1. Go to your repository's **Settings** tab (gear icon at the top)
2. In the left sidebar, scroll down and click **Pages**
3. Under **Source**, select:
   - **Deploy from a branch**
   - **Branch**: `main`
   - **Folder**: `/ (root)`
4. Click **Save**

#### Step 5: Get Your Shareable Link

1. Wait 1–2 minutes for GitHub to build the site
2. Refresh the Settings → Pages screen
3. You'll see a green banner: **Your site is live at:**

```
https://YOUR-USERNAME.github.io/aes-utilization-report/
```

4. Click the link to verify it works
5. **Share this URL** with your team

---

### OPTION B: Using Git Command Line (For Existing Git Users)

```bash
# 1. Create a new folder and initialize
mkdir aes-utilization-report
cd aes-utilization-report
git init

# 2. Copy all files from the package into this folder
#    - index.html
#    - README.md
#    - .nojekyll
#    - .gitignore

# 3. Add and commit
git add -A
git commit -m "Initial upload - AES Resource Utilization Report"

# 4. Create GitHub repo (using GitHub CLI, or create manually on github.com)
gh repo create aes-utilization-report --private --source=. --push

# OR if you created the repo manually on GitHub:
git remote add origin https://github.com/YOUR-USERNAME/aes-utilization-report.git
git branch -M main
git push -u origin main

# 5. Enable GitHub Pages
gh api repos/YOUR-USERNAME/aes-utilization-report/pages -X POST -f source.branch=main -f source.path=/
```

Then visit: `https://YOUR-USERNAME.github.io/aes-utilization-report/`

---

## Important Notes

### For Private Repositories (Confidential Data)

- GitHub Pages for **private repos** requires a **GitHub Pro**, **Team**, or **Enterprise** plan
- Free accounts can only use GitHub Pages on **public** repositories
- If you need to keep the data private, consider these alternatives:
  1. **GitHub Enterprise** (if PwC has a license) — private Pages supported
  2. **Azure Static Web Apps** (PwC likely has Azure) — see Alternative Hosting below
  3. **Remove embedded data** — upload the HTML without the Base64 data blob; users upload their own CSV each time

### Updating the Report

1. Go to your repository on GitHub
2. Click on `index.html`
3. Click the **pencil icon** (Edit) or use **Add file** → **Upload files** to replace it
4. Commit the changes
5. GitHub Pages will auto-update within 1–2 minutes

### Custom Domain (Optional)

If PwC has a custom domain, you can configure it under Settings → Pages → Custom domain.

---

## Alternative Hosting Options

### Azure Static Web Apps (Recommended for PwC)

If PwC has Azure access:

1. Go to **Azure Portal** → Create **Static Web App**
2. Connect to your GitHub repo
3. Set app location to `/`
4. Deploy — Azure gives you a URL like: `https://your-app.azurestaticapps.net`
5. Supports authentication via Azure AD (SSO with PwC credentials)

### SharePoint Workaround

If SharePoint blocks the file due to size or scripts:

1. Create a SharePoint page
2. Add a **"Embed" web part**
3. Paste the GitHub Pages URL into the embed code
4. This renders the dashboard inside SharePoint without uploading the file

### Netlify (Free Alternative)

1. Go to **https://app.netlify.com**
2. Drag and drop the entire package folder
3. Get an instant URL like: `https://random-name.netlify.app`
4. No account needed for a quick deploy

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Page shows 404 | Ensure `index.html` is in the repo root, not in a subfolder |
| Page shows README instead of dashboard | Check that the file is named exactly `index.html` (lowercase) |
| Changes not showing | GitHub Pages can take 1–5 minutes to update; hard refresh with Ctrl+Shift+R |
| "Pages disabled" error | Go to Settings → Pages and re-enable; select `main` branch |
| Private repo Pages not working | Requires GitHub Pro/Team/Enterprise plan; use public repo or Azure instead |
| Dashboard loads but no data | The Base64 data is embedded — if the file was truncated during upload, re-upload the complete file |

---

## File Checklist Before Upload

- [ ] `index.html` — The main dashboard (must be this exact filename)
- [ ] `README.md` — Repository documentation
- [ ] `.nojekyll` — Tells GitHub Pages not to process with Jekyll
- [ ] `.gitignore` — Excludes temp files

All files must be in the **root** of the repository.

---

*Guide prepared for PwC AES Oracle Practice | June 2026*
