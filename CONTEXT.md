# Director Tin — Project Context

## Step 1: Read the live repo before doing anything

Fetch this URL to get a directory listing of every file in the project:
https://api.github.com/repos/directortin/directortinnews/contents/

Each file in the response has a download_url. Fetch and read every file you find there. Do not rely on anything written below as a substitute for reading the actual live code — the files are the truth.

## Step 2: Things the repo files cannot tell you

### The admin panel
The owner manages the entire site through a local file called `admin.html` saved on their desktop. It is never uploaded to GitHub. It has three tabs:

- **Add Post** — owner fills in image, headline, optional caption, article URL, and date. The panel uploads the image file directly to the GitHub repo, then prepends a new post object to posts.json via the GitHub Contents API.
- **Manage Posts** — fetches posts.json, lists all posts with thumbnails. Owner can click any post to edit any field or delete it entirely. Changes are written back to posts.json only.
- **Settings** — fetches index.html, makes surgical CSS/text changes (colors, font sizes, grid columns, caption line limit, site caption text), and pushes the updated index.html back to GitHub. posts.json is never touched by the Settings tab.

The admin panel uses the GitHub Contents API with a personal access token hardcoded in the file. The token has repo read/write permissions.

### Key architectural rule
Posts are intentionally separated from the site design. index.html contains zero post data — it fetches posts.json at runtime and renders cards from it. This means index.html can be completely redesigned at any time without touching post data.

### The owner
Non-technical. Never ask them to write or edit code manually. All changes must be delivered as files they can download and either replace on GitHub via the pencil icon, or save to their desktop.

## Step 3: Stable facts
- GitHub owner: `directortin`
- GitHub repo: `directortinnews`
- The live site URL is whatever GitHub Pages serves from that repo
