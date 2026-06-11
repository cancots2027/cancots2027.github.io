# CANCOTS 2027 – Conference Website

Quarto website for the CANCOTS 2027 conference, deployed at **https://cancots2027.github.io**.

---

## Setup: Deploy to GitHub Pages

### Step 1 – Create the GitHub repo

You have two options for where to host the repo:

**Option A (recommended): GitHub Organization**
1. Go to github.com → your profile icon → **"Your organizations"** → **"New organization"**
2. Choose **Free**, name it exactly `cancots2027`
3. Inside the org, create a repo named exactly `cancots2027.github.io`

**Option B: Your personal account**
1. Create a repo named exactly `cancots2027.github.io` in your own account
2. (Works identically — GitHub routes it to the same URL either way)

### Step 2 – Enable GitHub Pages via GitHub Actions

In your new repo → **Settings → Pages**:
- Source: **GitHub Actions**
- (Don't select a branch — the workflow handles deployment)

### Step 3 – Push this project

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/cancots2027/cancots2027.github.io.git
git push -u origin main
```

The GitHub Actions workflow (`.github/workflows/deploy.yml`) will automatically:
1. Install Quarto
2. Run `quarto render`
3. Deploy the `_site/` output to GitHub Pages

Your site will be live at **https://cancots2027.github.io** within ~2 minutes of pushing.

---

## Local Development

Install [Quarto](https://quarto.org/docs/get-started/) then:

```bash
# Preview with live reload
quarto preview

# Build the site
quarto render
```

---

## File Structure

```
cancots2027.github.io/
├── _quarto.yml              ← Project config (title, URL, CSS, includes)
├── _includes/
│   ├── header.html          ← Shared header (logo, skyline, nav) – on every page
│   └── footer.html          ← Shared footer
├── _partials/
│   └── title-block.html     ← Suppresses Quarto's default title block
├── assets/
│   └── css/
│       └── style.css        ← All styles
├── .github/
│   └── workflows/
│       └── deploy.yml       ← Auto-deploy on push to main
├── index.qmd                ← Home page
├── theme.qmd                ← Theme & Papers
├── program.qmd              ← Program
├── about.qmd                ← About / Organizing Committee
├── local.qmd                ← Local Info
├── registration.qmd         ← Registration
└── notices.qmd              ← Notices & Announcements
```

## Customizing Content

**Conference details** (name, dates, location):
Search-and-replace across all `.qmd` files and `_includes/header.html`:
- `CANCOTS 2027` → your conference name/acronym
- `14–16 May 2027` → your dates
- `Toronto, Canada` → your city

**Contact email**: Replace `cancots2027@example.com` everywhere.

**Nav active state**: Each page's nav link gets `class="active"` automatically via CSS
(matching the current filename). To add this, open `_includes/header.html` and add
`class="active"` to the relevant `<a>` tag — or use a Quarto `page-navigation` shortcode.

**Adding a new page**:
1. Copy any `.qmd` file (e.g. `about.qmd`)
2. Update the YAML frontmatter (`title`, `pagetitle`)
3. Add a link in `_includes/header.html`

**Sidebar images**: Replace the Wikipedia image URLs in `index.qmd` and `local.qmd`
with your own photos (add them to `assets/images/`).

**Colors**: Edit the CSS tokens at the top of `assets/css/style.css`.
