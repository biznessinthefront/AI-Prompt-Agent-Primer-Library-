# 🚀 GitHub Deployment Guide

This guide walks you through deploying your AI Prompt Library to GitHub and GitHub Pages.

## 📋 Prerequisites

- GitHub account (free)
- Git installed on your computer ([Download Git](https://git-scm.com/downloads))
- Your Firebase configuration completed (see SETUP_GUIDE.md)

## Step 1: Create a GitHub Repository

1. Go to [GitHub.com](https://github.com) and sign in
2. Click the **+** icon in the top right → **New repository**
3. Repository settings:
   - **Repository name**: `ai-prompt-library` (or your preferred name)
   - **Description**: "A collaborative library for AI prompts and agent configurations"
   - **Visibility**: Public (recommended) or Private
   - **Do NOT** initialize with README, .gitignore, or license (we already have these)
4. Click **Create repository**

## Step 2: Prepare Your Local Files

Before uploading, make sure you've completed Firebase setup:

1. ✅ Created Firebase project
2. ✅ Added Firebase config to both `index.html` and `admin.html`
3. ✅ Set up Firestore security rules
4. ✅ Enabled authentication
5. ✅ Created your first admin user

## Step 3: Initialize Git Locally

Open your terminal/command prompt in the project folder and run:

```bash
# Navigate to your project folder
cd path/to/ai-prompt-library

# Initialize git repository
git init

# Add all files
git add .

# Commit the files
git commit -m "Initial commit: AI Prompt & Agent Library"
```

## Step 4: Connect to GitHub

Replace `YOUR_USERNAME` and `REPO_NAME` with your actual GitHub username and repository name:

```bash
# Add the remote repository
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git

# Push to GitHub
git branch -M main
git push -u origin main
```

**Note:** You may be prompted to log in to GitHub. Use your GitHub credentials.

## Step 5: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** (top menu)
3. In the left sidebar, click **Pages**
4. Under "Source":
   - Select branch: **main**
   - Select folder: **/ (root)**
5. Click **Save**
6. Wait 2-3 minutes for deployment
7. Your site will be live at: `https://YOUR_USERNAME.github.io/REPO_NAME/`

## Step 6: Test Your Deployment

1. Visit your GitHub Pages URL
2. Try browsing the library
3. Submit a test prompt
4. Go to `/admin.html` and log in
5. Approve your test submission

## 🎉 You're Live!

Your library is now publicly accessible! Share the URL with your team.

## 📝 Making Updates

Whenever you want to update your site:

```bash
# Make your changes to the files

# Stage the changes
git add .

# Commit with a descriptive message
git commit -m "Description of your changes"

# Push to GitHub
git push
```

GitHub Pages will automatically redeploy (usually within 1-2 minutes).

## 🔧 Common Issues

### "Permission denied (publickey)"

You need to set up SSH keys or use HTTPS authentication:

```bash
# Use HTTPS instead
git remote set-url origin https://github.com/YOUR_USERNAME/REPO_NAME.git
```

### "Repository not found"

Double-check:
- Repository name is correct
- URL matches your GitHub repository
- You have access to the repository

### Changes not appearing on site

- Wait 2-3 minutes after pushing
- Hard refresh your browser (Ctrl+Shift+R or Cmd+Shift+R)
- Check GitHub Actions tab for deployment status

### Firebase not working on deployed site

- Verify Firebase config is correct in both HTML files
- Check browser console for errors
- Ensure Firestore rules are published
- Verify your domain is authorized in Firebase Console → Authentication → Settings

## 🌐 Custom Domain (Optional)

Want to use your own domain instead of `.github.io`?

1. Buy a domain (Namecheap, Google Domains, etc.)
2. In your repo, create a file named `CNAME` with your domain:
   ```
   yourdomain.com
   ```
3. In your domain registrar, add DNS records:
   - Type: A
   - Host: @
   - Value: 185.199.108.153
   - (Add 3 more A records with: 185.199.109.153, 185.199.110.153, 185.199.111.153)
4. Wait for DNS propagation (up to 24 hours)
5. In GitHub repo Settings → Pages, add your custom domain

## 📊 Analytics (Optional)

Want to track visitors?

1. Get a Google Analytics tracking ID
2. Add this code before `</head>` in both HTML files:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_TRACKING_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_TRACKING_ID');
</script>
```

## 🔒 Security Notes

**Safe to commit:**
- HTML files with Firebase config (frontend apps are public)
- README and documentation
- .gitignore and LICENSE

**Never commit:**
- Admin passwords
- Private API keys
- Service account credentials
- `.env` files with secrets

## 🆘 Need Help?

- Check [GitHub Pages documentation](https://pages.github.com/)
- Open an issue in your repository
- Search for solutions on Stack Overflow

---

Congratulations! Your AI Prompt Library is now live on GitHub! 🎊
