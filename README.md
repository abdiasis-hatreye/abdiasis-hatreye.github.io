# Abdiasis Suleiman Hatreye — Portfolio

A fast, responsive, single-file portfolio website (HTML5 + CSS3 + vanilla JavaScript), ready for GitHub Pages. No backend, no build step, no paid hosting.

## Project structure

```
index.html   ← the whole website: HTML, CSS (in <style>) and JavaScript (in <script>)
README.md    ← this guide
(optional)   profile.jpg, Abdiasis-Hatreye-CV.pdf, favicon.png, og-image.png
```

Inside `index.html`:

| Part | Where |
|---|---|
| SEO + Open Graph tags, favicon | top of `<head>` |
| Colours, fonts, spacing (design tokens) | `:root { … }` at the start of `<style>` |
| Sections: Home, About, Services, Skills, Projects, GitHub, Education & Goals, Contact, Footer | `<body>`, each marked with a `<!-- ===== NAME ===== -->` comment |
| **Your links and details** | the `CONFIG` object at the start of `<script>` |

## Editing your details

Open `index.html` and find `const CONFIG = {` near the bottom. Fill in the values between the quotes:

```js
githubUsername: "your-username",                          // GitHub buttons + live repo list
linkedinUrl:    "https://www.linkedin.com/in/your-profile",
email:          "you@example.com",                        // becomes a working mailto: link
whatsappNumber: "",                                       // optional, digits only incl. country code
photo:          "profile.jpg",                            // optional; otherwise "AH" initials are shown
cvFile:         "Abdiasis-Hatreye-CV.pdf",                // optional; the Download CV button appears only when set
projects: {
  kasmo:     { repo: "https://github.com/you/kasmo-system", demo: "" },
  hatreyeai: { repo: "https://github.com/you/hatreye-ai",   demo: "" },
  adeeg:     { repo: "https://github.com/you/adeeg",        demo: "" }
},
featuredRepos: []   // optional list of repo names to pin in the GitHub section
```

Anything left as `""` shows a neutral "coming soon" note instead of a broken link, so nothing on the page pretends to work.

- **Name / text:** search for the text in `index.html` and edit it directly.
- **Profile photo:** put a square image (e.g. 600×600 `profile.jpg`) next to `index.html`, then set `photo: "profile.jpg"`.
- **ADEEG tech stack:** in the ADEEG project card, replace `<li class="placeholder">Tech stack coming soon</li>` with tags, e.g. `<li class="tag">Laravel</li>`.
- **Project status:** each card has `<span class="status">Concept</span>`; for a live project use `<span class="status live"><span class="pulse" aria-hidden="true"></span>Live</span>`.
- **Favicon:** put `favicon.png` next to `index.html` and follow the comment above the `<link rel="icon">` line.
- **Social preview:** after deploying, uncomment the `og:url` (and optionally `og:image`) lines in `<head>` and put in your real site URL.
- **Colours & fonts:** change the variables in `:root` at the top of `<style>` — `--gold` (main accent), `--copper` (second accent), `--bg` (background), `--display` / `--font` (fonts).
- **Sections:** Home, About, Services ("How I can help"), Skills, Projects (KASMO is the large featured card), GitHub, Education & Goals, Contact. Each is marked with a `<!-- ===== NAME ===== -->` comment.

## Deploying to GitHub Pages

### Option A — personal site (`https://USERNAME.github.io`)

1. Sign in to GitHub → **+** (top right) → **New repository**.
2. Name it exactly `YOUR-GITHUB-USERNAME.github.io`, set it **Public**, click **Create repository**.
3. Click **uploading an existing file** (or **Add file → Upload files**), drag in `index.html` (and any photo/CV files).
4. Write a commit message such as `Add portfolio` and click **Commit changes**.
5. Open **Settings → Pages**.
6. Under **Build and deployment**, set **Source: Deploy from a branch**, **Branch: `main`**, folder **`/ (root)`**, then **Save**.
7. Wait 1–3 minutes and refresh the Pages settings page. The address appears at the top ("Your site is live at …"): `https://YOUR-GITHUB-USERNAME.github.io/`.

### Option B — project site (`https://USERNAME.github.io/REPO-NAME/`)

Same steps, but use any repository name (e.g. `portfolio`) or an existing repository. Make sure `index.html` is in the **root** of the `main` branch, then configure **Settings → Pages** as in step 6. The site will be at `https://YOUR-GITHUB-USERNAME.github.io/REPO-NAME/`.

### Using Git from the command line (optional)

```bash
git init
git add index.html README.md
git commit -m "Add portfolio"
git branch -M main
git remote add origin https://github.com/YOUR-GITHUB-USERNAME/YOUR-GITHUB-USERNAME.github.io.git
git push -u origin main
```

### Updating the site later

Edit `index.html` (on GitHub click the file → pencil icon, or edit locally and push), commit, and GitHub Pages redeploys automatically within a few minutes. The **Actions** tab shows each deployment.

### Troubleshooting

| Problem | Fix |
|---|---|
| 404 "There isn't a GitHub Pages site here" | Wait a few minutes; check Settings → Pages shows branch `main` and `/ (root)`; the file must be named exactly `index.html` (lowercase) in the root. |
| Old version still showing | Hard refresh (Ctrl+F5) or open in a private window; check the latest run in the **Actions** tab finished. |
| Photo / CV not loading | File names are case-sensitive on GitHub Pages: `Profile.JPG` ≠ `profile.jpg`. |
| Repo list says it couldn't load | Check `githubUsername` is spelled right. GitHub's public API allows ~60 requests/hour per visitor; the page falls back to a link automatically. |
| Pages option missing | Private repos need a paid plan for Pages; make the repository Public. |

## Final checklist

- [ ] `CONFIG` filled in: GitHub username, LinkedIn URL, email
- [ ] Project repository links added (demo links only if a real demo exists)
- [ ] ADEEG technologies added
- [ ] Optional: photo, CV file, favicon, `og:url`
- [ ] No yellow placeholders left on the page
- [ ] Mobile: open on a phone — menu opens/closes, no sideways scrolling, buttons easy to tap
- [ ] Navigation: every menu link scrolls to its section; active link highlights while scrolling
- [ ] Links: GitHub, LinkedIn, email and repo buttons open the right pages
- [ ] Accessibility: Tab through the page — focus outline is visible on every link and button; Esc closes the mobile menu
- [ ] Deployment: Settings → Pages shows "Your site is live", and the URL loads
