# AGENTS: Maintenance Instructions for the Blog

This document describes how automated agents (Codex, GPT, etc.) should
maintain this static HTML blog.  
All changes must follow these rules exactly to avoid breaking GitHub Pages.

---

# 1. File Structure Rules

The site follows a simple static structure:


index.html → homepage with list of posts
post-*.html → individual blog posts
sitemap.xml → search-engine sitemap
robots.txt → SEO instructions
404.html → custom error page
assets/ → optional static assets
AGENTS.md → automation instructions (this file)


New blog posts must follow this naming convention:


Example:  
`post-building-my-iaas.html`

The `<slug>` should be:

- lowercase  
- hyphen-separated  
- no spaces  
- only letters, numbers, and hyphens  

---

# 2. Creating New Blog Posts (REQUIRED STEPS)

Whenever an agent creates a new blog post:

## **Step A — Generate the post file**

Create a new file at the repo root:


It must include:

- `<title>` matching the post title
- A main `<h1>`
- A publication date inside the HTML (ISO format recommended)
- Optional Bootstrap layout structure copied from existing posts

---

## **Step B — Add a link to the homepage**

Open `index.html` and insert a new post card entry inside the posts list.

Follow the same structure as existing posts:

Example:

```html
<a href="post-my-new-post.html" class="text-decoration-none text-dark">
  <div class="card mb-4 post-card">
    <div class="card-body">
      <h3 class="h5">My New Post Title</h3>
      <p class="small text-muted mb-2">
        YYYY-MM-DD · X min read ·
        <span class="tag bg-primary text-white">Blog</span>
      </p>
      <p>
        A short 1–2 sentence summary of the post.
      </p>
    </div>
  </div>
</a>


Insertion position:

Insert the newest post at the top of the list.

Do not remove or reorder older posts.

3. Updating the Sitemap (REQUIRED)

Every new post must also be added to sitemap.xml.

Append a new <url> block like this:

```
<url>
  <loc>https://ryanrslater.github.io/post-<slug>.html</loc>
</url>

```

The sitemap structure:

```
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">

  <!-- homepage -->
  <url>
    <loc>https://ryanrslater.github.io/</loc>
    <priority>1.0</priority>
  </url>

  <!-- existing posts here -->

  <!-- new post (append below existing ones) -->
  <url>
    <loc>https://ryanrslater.github.io/post-<slug>.html</loc>
  </url>

</urlset>
```s

Notes:

Do not remove old links.

Keep indentation consistent.

