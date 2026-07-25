# Juno Bug Pottery — Website Guide

This is my living reference doc for how my website works. Whenever I want to
make a change and don't remember how, I read this file first (or hand it to
Claude and ask). Claude should keep this file up to date as we make changes.

Last updated: 2026-07-26

## The big picture

- The site is a **plain static website** — just HTML, CSS, and image files.
  No database, no e-commerce, no build tools.
- It's a **photo gallery only**. Visitors browse pottery by category. To buy,
  they click through to my Etsy and/or Felt shop.
- It's hosted for **free on GitHub Pages**, with my own domains
  (`junobug.com` and `junobug.co.nz`, bought on GoDaddy) pointed at it.
- Why this instead of Squarespace: no monthly fee, and Claude can build/edit
  it directly. The tradeoff I accepted: adding new photos means a short git
  workflow (below) instead of a drag-and-drop editor.

## Current status

- [x] Site pages built locally (2026-07-26)
- [x] Local git repo created (2026-07-26)
- [ ] Pushed to GitHub
- [ ] GitHub Pages turned on
- [ ] junobug.com / junobug.co.nz connected via GoDaddy DNS
- [ ] Real photos added (site currently uses "Photo coming soon" placeholders)
- [ ] Etsy shop link added
- [ ] Felt shop link added

*(Claude: tick these off and update the date above as we complete each step.)*

## Folder structure

```
Juno Bug Pottery/
├── index.html          ← home page
├── mugs-cups.html       ← one page per category
├── bowls.html
├── plates.html
├── vases.html
├── canisters.html
├── tiles.html
├── css/
│   └── style.css        ← all the styling, shared by every page
├── images/
│   ├── placeholder.svg   ← "photo coming soon" graphic
│   ├── mugs-cups/        ← put mug/cup photos here
│   ├── bowls/             ← put bowl photos here
│   ├── plates/
│   ├── vases/
│   ├── canisters/
│   └── tiles/
└── WEBSITE-GUIDE.md      ← this file
```

## How to add a new pottery photo

1. Take/export the photo. Keep the file size reasonable (under ~1–2 MB —
   resize/compress if your camera photos are huge).
2. Drop the photo file into the right folder, e.g. `images/bowls/` for a bowl.
   Use a simple lowercase name with no spaces, e.g. `blue-speckled-bowl.jpg`.
3. Open the matching page (e.g. `bowls.html`) in a text editor (VS Code).
4. Find the `<div class="photo-grid">` section. Copy one whole block that
   looks like this:
   ```html
   <figure>
     <img src="images/placeholder.svg" alt="Bowl photo coming soon">
     <figcaption>Example bowl — replace this photo and caption</figcaption>
   </figure>
   ```
5. Paste a new copy just before the closing `</div>`, then edit it:
   - `src="images/bowls/blue-speckled-bowl.jpg"`
   - `alt="..."` → a short description (for accessibility/screen readers)
   - the `<figcaption>` text → whatever caption you want visitors to see
     (name, size, price-on-request, whatever)
6. Save, then publish the change (see "Publishing changes" below).

To remove a photo, delete its whole `<figure>...</figure>` block and delete
the image file from the folder.

## Adding a whole new category

1. Copy an existing page, e.g. `bowls.html`, and rename the copy
   (e.g. `planters.html`).
2. Create a matching folder: `images/planters/`.
3. In the new page, change the `<title>`, the `<h1>`, and remove the example
   placeholder `<figure>` blocks once you have real photos.
4. In **every** page's `<nav class="site-nav">` list (including `index.html`),
   add a matching `<li><a href="planters.html">Planters</a></li>` line.
5. On `index.html`, also add a matching card in the `<section class="category-grid">`.
6. Publish the change (see below).

## Previewing changes before publishing

Double-click any `.html` file (e.g. `index.html`) to open it in your browser
and see your changes. This works entirely offline — nothing goes live until
you publish.

## Publishing changes (pushing to GitHub)

Every time you want your changes to appear on junobug.com, run these three
commands from this folder in a terminal:

```
git add .
git commit -m "describe what you changed, e.g. add new bowl photos"
git push
```

GitHub Pages picks up the change automatically — it usually shows up on the
live site within a minute or two.

## GitHub account details

- GitHub sign-in email: sanet@lonrix.com
- GitHub username: Sanet1313
- Repository name: *(to fill in)*
- Repository URL: *(to fill in)*

## Domains

- junobug.com — bought on GoDaddy
- junobug.co.nz — bought on GoDaddy
- DNS setup notes: *(to fill in once we configure this)*

## Shop links

- Etsy shop URL: *(to fill in)*
- Felt shop URL: *(to fill in)*

Once I have these, update the `href="#"` placeholders in the "Shop on Etsy" /
"Shop on Felt" buttons on every page.

## Categories

Mugs & Cups, Bowls, Plates, Vases, Canisters, Tiles
