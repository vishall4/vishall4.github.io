# Vishal Lohiya

Intuition first. Formulas second.

Personal website — notes, breakdowns, and findings on the fundamentals of data science and machine learning.

**Live at:** [vishall4.github.io](https://vishall4.github.io)

Built with [Jekyll](https://jekyllrb.com/) + [GitHub Pages](https://pages.github.com/).

---

## Adding a New Post

1. Create a new file in `_posts/`
2. Name it: `YYYY-MM-DD-your-post-title.md`
3. Add this at the top:

layout: post
title: "Your Post Title"
date: 2025-03-01
tags: [Mathematics, Statistics]
excerpt_text: "A one-line description for the homepage."

4. Write your content below in Markdown
5. Commit and push — site updates in ~2 minutes

## Adding Images to Posts

1. Put images in `assets/images/`
2. Reference in posts: `![description](/assets/images/your-image.png)`

## Site Structure

_config.yml - Site settings
_layouts/default.html - Base template
_layouts/post.html - Blog post template
_posts/ - Blog posts (Markdown)
assets/css/style.css - Styles
assets/images/ - Post images
index.html - Homepage
about.md - About page
blog.md - Blog listing
Gemfile - Dependencies

## Custom Domain (Optional)

1. Buy a domain from Namecheap or Cloudflare (~$10-15/year)
2. Repo Settings → Pages → Custom domain → enter your domain
3. Add DNS records at your registrar:
   - CNAME: `www` → `vishall4.github.io`
   - A records pointing to GitHub's IPs
4. Wait for DNS propagation (~30 min to 24 hours)
