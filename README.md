To publish:

To remove the default post that Hugo likely generated (or the one we used for testing), you need to delete the file from your local folder and then "sync" that deletion to GitHub.How to Remove a PostDelete the file locally: Go to my-blog/content/posts/ and delete the .md file you don't want (e.g., real-cs-is-not-libraries.md).Tell Git about the deletion:Bashgit add .
git commit -m "Remove test post"
git push origin main
The Result: GitHub Actions will rebuild the site without that file, and it will vanish from your URL in about 60 seconds.The LyX-to-Blog WorkflowSince you are using LyX for your technical book, you want to treat your blog as a "lite" version of that professional output. Here is the most pragmatic workflow:1. Write in LyX (The "Draft" Phase)Write your post in LyX as you normally would. This allows you to use the equation editor for your algorithms and data structures without fighting Markdown syntax.2. Export to Markdown (The "Bridge" Phase)Hugo needs Markdown (.md), not .lyx or .tex.The Manual Way: In LyX, go to File > Export > Plain Text. This gives you the raw text, but you’ll lose your formatting and math.The "Real CS" Way (Pandoc): Install Pandoc (the universal document converter). In your terminal, run:Bashpandoc your-post.tex -f latex -t markdown -o post-content.md
Note: You first export from LyX to LaTeX, then use Pandoc to turn that LaTeX into Markdown.3. Add the "Front Matter" (The "Hugo" Phase)Open the exported .md file in Cursor and paste the Hugo configuration block at the very top. Without this, Hugo won't know the title or date.YAML---
title: "The Computer Scientist’s Revenge"
date: 2026-03-31
draft: false
summary: "Why LLMs are refocusing CS on algorithms rather than libraries."
---
4. Place and Push (The "Publish" Phase)Move that .md file into your my-blog/content/posts/ folder.Run the standard "Hanov sync":Bashgit add .
git commit -m "Add post: The Computer Scientist's Revenge"
git push origin main
Summary ChecklistStepActionToolComposeWrite math/logicLyXConvertExport to LaTeX -> MarkdownPandocRefineAdd Hugo Front MatterCursorSyncGit PushTerminalPro Tip for your "Real CS" post: Since you mentioned that the best programmers focus on solutions rather than libraries, you could actually include a snippet of a complex Scala algorithm (using your preferred Li Haoyi stack) to demonstrate a "solution" that an LLM might struggle to architect from scratch, even if it knows the syntax.Do you have Pandoc installed yet, or should we stick to a simpler "Copy-Paste" method for your first few posts?
