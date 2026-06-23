# Akhil Kora — Profile & Build Log

A personal **maker profile** with a built-in **blog**. This is a plain static site — no build step — so it works two ways:

- **Open it locally:** double-click `index.html`. Navigate to the blog, open a post, and the design PDFs load inline.
- **Deploy to GitHub Pages:** push the contents of this folder; it serves as-is.

## Structure

```
index.html                         ← the maker profile (homepage)
blog/index.html                    ← build log (post list)
blog/2026/05/.../index.html        ← Coaxial Swerve Drivetrain (embeds PDF)
blog/2026/04/.../index.html        ← Coaxial vs. Differential (embeds PDF)
blog/2026/03/.../index.html        ← First CNC Cuts (article)
about/index.html                   ← about page
assets/css/style.css               ← shared dark "maker" theme
assets/docs/*.pdf                   ← the embedded design documents
.nojekyll                          ← tells GitHub Pages to serve files as-is
```

## Deploy to GitHub Pages

```bash
cd site
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/<you>/<repo>.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`**.
Because all links are **relative**, the site works whether it's served at the domain root
(`<you>.github.io`) or in a project subfolder (`<you>.github.io/<repo>`) — no config to change.

## Add a new blog post

1. Copy an existing folder under `blog/2026/...` to a new dated path.
2. Edit the title, date, and body. For a document post, drop the PDF in `assets/docs/`
   and point the three `assets/docs/...pdf` references at it.
3. Add a matching `<a class="post-card">` card to `blog/index.html` (and, if you want it
   on the homepage, to the Blog section of `index.html`).

## Update the profile

`index.html` is the self-contained, exported homepage (it has no external dependencies and
needs no build step — that's why it works on GitHub Pages). The blog and about pages are
plain static HTML that link back to `index.html`. There is intentionally **no `.dc.html`
source file in this folder** — that file is the editable design source and renders as raw
`{{ }}` placeholders if served directly, so it must not be deployed.
