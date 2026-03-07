# Director Tin — Claude Context

## About the site
The owner runs an Instagram and TikTok news page called Director Tin (@directortin). They post images of news stories on social media, and this website exists so followers can find the full article behind each post. Each card on the site shows the post image, a headline, an optional caption summary, the date, and a link to the full news article. The site URL lives in the Instagram and TikTok bios.

## About the admin panel
This file lives on the owner's desktop only — it is never uploaded to GitHub. It talks directly to the GitHub Contents API using a hardcoded personal access token with repo read/write permissions. It has three tabs:

**Add Post tab:**
- Owner fills in: post image, headline, optional caption, article URL, date
- On publish: image is uploaded as a file to the repo, then a new post object is prepended to posts.json
- posts.json is the only file modified when adding a post

**Manage Posts tab:**
- Fetches posts.json fresh from GitHub every time the tab is opened
- Lists all posts with thumbnail, headline, and date
- Owner clicks any post to edit any field or delete it entirely
- All changes write back to posts.json only

**Settings tab:**
- Fetches the live index.html from GitHub
- Controls: background color, card color, caption line limit, headline font size, desktop grid column count, site caption text
- Makes surgical find/replace changes to index.html and pushes it back
- posts.json is never touched by the Settings tab

**Export for Claude button:**
- Fetches the GitHub repo directory listing
- Downloads every text file and bundles them into context_bundle.txt
- Owner uploads this file to start a new Claude chat with full context

## Variables to verify with owner
All of the following may be outdated. Verify every one before proceeding.

1. Platforms: Instagram and TikTok
2. Site purpose: followers visit this site to find the full news article behind each post
3. Owner is non-technical — never ask them to edit code, always deliver ready-to-use downloadable files

## Your first response
Structure your response in exactly this order:

**Section 1** — heading "Here is everything I learned from your code files:"
Summarise only what the code taught you: architecture, each file's role, design, data structures, how the site renders. Nothing from this context file.

**Section 2** — heading "Here is what I learned from your context file:"
List only what came from this file. Nothing from the code.

**Section 3** — heading "Please confirm these variables are still accurate:"
Number each variable above and ask the owner to confirm or correct. Stop here. Do not ask what they want to work on until every variable is confirmed.
