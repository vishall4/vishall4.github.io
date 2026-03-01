# Vishal Lohiya — Personal Website

Teaching maths the way I wish someone would've taught me — like a story, not a formula sheet.

Built with [Jekyll](https://jekyllrb.com/) and hosted on [GitHub Pages](https://pages.github.com/).

---

## 🚀 How to Deploy (Step by Step)

### Step 1: Create a GitHub Account
If you don't have one, go to [github.com](https://github.com) and sign up.

### Step 2: Create a New Repository
1. Click the **+** button (top right) → **New repository**
2. Name it **exactly**: `yourusername.github.io` (replace `yourusername` with your actual GitHub username)
   - Example: if your username is `vishallohiya`, the repo name is `vishallohiya.github.io`
3. Make it **Public**
4. Do NOT initialize with README (we already have one)
5. Click **Create repository**

### Step 3: Upload Your Site Files
**Option A — Using GitHub's web interface (easiest):**
1. On your new repo page, click **"uploading an existing file"**
2. Drag and drop ALL the files and folders from this site folder
3. Click **Commit changes**

**Option B — Using Git from terminal (recommended to learn):**
```bash
# Install Git if you haven't: https://git-scm.com/downloads

# Navigate to your site folder
cd path/to/your/jekyll-site

# Initialize git
git init
git add .
git commit -m "Initial site launch"

# Connect to your GitHub repo
git remote add origin https://github.com/yourusername/yourusername.github.io.git

# Push
git branch -M main
git push -u origin main
```

### Step 4: Enable GitHub Pages
1. Go to your repo on GitHub
2. Click **Settings** → **Pages** (in the left sidebar)
3. Under **Source**, select **Deploy from a branch**
4. Select **main** branch, **/ (root)** folder
5. Click **Save**

### Step 5: Wait ~2 minutes
Your site will be live at: `https://yourusername.github.io`

---

## 📝 How to Add a New Post

1. Create a new file in the `_posts/` folder
2. Name it: `YYYY-MM-DD-your-post-title.md` (e.g., `2025-03-01-chi-squared.md`)
3. Add this at the top:
```yaml
---
layout: post
title: "Your Post Title"
date: 2025-03-01
tags: [Mathematics, Statistics]
excerpt_text: "A one-line description for the homepage."
---
```
4. Write your post content below in Markdown
5. Push to GitHub (or upload via web interface)

---

## 🔧 How to Customize

### Update your info:
- Edit `_config.yml` to change your name, description, and social links
- Edit `about.md` to update your about page
- Edit `index.html` to change the homepage hero text

### Add images to posts:
1. Put images in `assets/images/`
2. Reference in posts: `![description](/assets/images/your-image.png)`

### Add a custom domain:
1. Buy a domain from Namecheap, Cloudflare, or similar (~$10-15/year)
2. In your GitHub repo: Settings → Pages → Custom domain → enter your domain
3. At your domain registrar, add DNS records:
   - Type: CNAME, Name: www, Value: yourusername.github.io
   - Type: A records pointing to GitHub's IPs (GitHub docs will show these)
4. Wait for DNS propagation (~30 min to 24 hours)

---

## 📁 Site Structure

```
jekyll-site/
├── _config.yml          # Site settings (name, links, etc.)
├── _layouts/
│   ├── default.html     # Base template
│   └── post.html        # Blog post template
├── _posts/
│   ├── 2025-02-20-degrees-of-freedom.md
│   ├── 2025-02-24-gamma-function.md
│   └── 2025-02-27-poisson-distribution.md
├── assets/
│   ├── css/
│   │   └── style.css    # All styles
│   └── images/          # Post images go here
├── index.html           # Homepage
├── about.md             # About page
├── blog.md              # Blog listing page
├── Gemfile              # Ruby dependencies
└── README.md            # This file
```

---

## Moving to Hugo Later

If you ever want to switch to Hugo:
1. Your Markdown posts transfer directly (just copy them)
2. Pick a Hugo theme
3. Adjust the folder structure (Hugo uses `content/posts/` instead of `_posts/`)
4. Update config file format (TOML instead of YAML)

Total migration time: ~30 minutes for a small site.
