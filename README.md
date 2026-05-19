# Guo Cheng — Personal Website

A static personal website at
<https://drguocheng.github.io>, built with plain HTML + CSS so it can
be hosted on **GitHub Pages** for free.

## Files in this folder

```
index.html          ← landing page (About / News / Research / Projects)
publications.html   ← publications page
hiring.html         ← prospective Ph.D. students page
assets/style.css    ← stylesheet
assets/profile.jpg  ← REPLACE with your own portrait (any square-ish JPG/PNG)
CV_GCheng.pdf       ← OPTIONAL: drop your CV here so the homepage link works
.nojekyll           ← tells GitHub Pages to serve files as-is (no Jekyll)
README.md           ← this file
```

## Before you push

1. **Add a profile photo.** Put a square-ish photo at `assets/profile.jpg`
   (about 400 × 400 px works well). If you keep a different filename, update
   the `<img>` tag in `index.html`.
2. **Add your CV (optional).** Copy your CV PDF into this folder and name it
   `CV_GCheng.pdf` so the "CV (PDF)" link on the homepage works.
3. **Fix the GitHub link.** Both `index.html` and the other pages currently
   point to `https://github.com/dashboard` (your personal dashboard URL). When
   you make a public profile, change those four links to
   `https://github.com/<your-username>`.

## Deploying to GitHub Pages — terminal only

GitHub Pages serves a site automatically for any repository named
`<your-username>.github.io`. There is **no UI step required**.

Below, replace `YOUR-USERNAME` with your real GitHub username
(e.g. `guocheng`). The whole process is two pieces:
*create the repo on GitHub*, then *push these files to it from your terminal.*

### 1. Create the empty repo on GitHub (one-time)

You can do this entirely from the terminal with the
[GitHub CLI](https://cli.github.com/). If `gh` is not installed:

```bash
# macOS
brew install gh
# Ubuntu / Debian
sudo apt install gh
# or follow https://cli.github.com/manual/installation
```

Then authenticate (only the first time):

```bash
gh auth login          # choose GitHub.com → HTTPS → Login with a browser
```

Create the repo (must be named `<username>.github.io` for a user site):

```bash
gh repo create YOUR-USERNAME.github.io --public --description "Personal website"
```

> **No `gh`?** Open <https://github.com/new>, create a **public** repo named
> exactly `YOUR-USERNAME.github.io`, leave it empty (no README, no .gitignore),
> then return to your terminal.

### 2. Push this folder to GitHub

From the terminal, `cd` into this directory and run:

```bash
git init -b main
git add .
git commit -m "Initial commit: personal website"

# Use HTTPS (works everywhere; gh sets up a credential helper for you)
git remote add origin https://github.com/YOUR-USERNAME/YOUR-USERNAME.github.io.git

# …or use SSH if you have an SSH key set up
# git remote add origin git@github.com:YOUR-USERNAME/YOUR-USERNAME.github.io.git

git push -u origin main
```

That's it. In 30–90 seconds your site will be live at:

```
https://YOUR-USERNAME.github.io/
```

You can confirm the build status with:

```bash
gh run list --limit 5
gh run view --log
```

### 3. Updating the site later

Edit any HTML/CSS file, then:

```bash
git add -A
git commit -m "Update: <what you changed>"
git push
```

GitHub Pages will rebuild automatically.

## Local preview (optional)

To preview the site locally without any build step:

```bash
# Python (any version with python3)
python3 -m http.server 8000
# then open http://localhost:8000 in your browser
```

Or just open `index.html` directly in your browser — it works without a server.

## Why `.nojekyll`?

GitHub Pages runs files through Jekyll by default, which can hide files whose
names start with `_`. The empty `.nojekyll` file in this repo turns Jekyll off
so every file is served exactly as written.

## Customizing

- **Add a news item:** edit the `<ul>` inside `<section class="news">` in
  `index.html`. Each entry is one `<li>` with a `<span class="date">` and a
  `<span>` for the body.
- **Add a publication:** add a new `<li>` to the appropriate `.pub-list` in
  `publications.html`. Wrap your name in `<span class="me">G. Cheng</span>` so
  it bolds correctly.
- **Add a project card:** copy one of the `<div class="project">` blocks in
  `index.html` and edit it.
- **Change colors:** edit the `:root { … }` block at the top of
  `assets/style.css`.

— Built 2026
