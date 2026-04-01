# My Blog (Hugo + PaperMod)

A professional blog built with Hugo and the PaperMod theme, integrated with GitHub Actions for automated deployment.

## 🚀 Publishing Guide

### How to Remove a Post
To remove a post (e.g., a default or test post), delete the local file and sync the deletion to GitHub.

1. **Delete locally**:
   ```bash
   rm content/posts/your-post.md
   ```
2. **Sync with Git**:
   ```bash
   git add .
   git commit -m "Remove test post"
   git push origin main
   ```
*The site will rebuild automatically via GitHub Actions and update in ~60 seconds.*

---

## ✍️ LyX-to-Blog Workflow

This workflow treats the blog as a "lite" version of your professional LyX output.

### 1. Write in LyX (Draft)
Write your post in LyX as usual. This allows you to use the equation editor for algorithms and data structures.

### 2. Export to Markdown (Bridge)
Hugo requires Markdown (`.md`).
- **Export from LyX**: `File > Export > LaTeX (plain)`.
- **Convert with Pandoc**:
  ```bash
  pandoc your-post.tex -f latex -t markdown -o post-content.md
  ```

### 3. Add Front Matter (Hugo)
Add the Hugo configuration block to the top of your exported `.md` file.

```yaml
---
title: "The Computer Scientist’s Revenge"
date: 2026-03-31
draft: false
summary: "Why LLMs are refocusing CS on algorithms rather than libraries."
---
```

### 4. Place and Push (Publish)
1. Move the `.md` file to `content/posts/`.
2. Sync with Git:
   ```bash
   git add .
   git commit -m "Add post: [Post Title]"
   git push origin main
   ```

---

## 📋 Summary Checklist

| Step | Action | Tool |
| :--- | :--- | :--- |
| **Compose** | Write math/logic | LyX |
| **Convert** | Export to LaTeX -> Markdown | Pandoc |
| **Refine** | Add Hugo Front Matter | Editor |
| **Sync** | Git Push | Terminal |

---

## 💡 Pro Tip: "Real CS" Posts
Focus on solutions rather than libraries. Include snippets of complex Scala algorithms (e.g., using the Li Haoyi stack) to demonstrate architectural depth that LLMs might struggle to replicate.

---

### Setup Note
Do you have Pandoc installed? If not, you can use a simpler "Copy-Paste" method for your first few posts.
