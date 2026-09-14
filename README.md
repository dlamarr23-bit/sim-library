# Physical Science 8 — Sim Library

A static site with 31 interactive physics/chemistry simulations, organized by
the same units and topics as the Physical Science 8 textbook. `index.html` is
the table-of-contents page; every simulation lives in its own folder with its
own `index.html` so it gets a clean URL (e.g. `/position-time-graphs/`).

This whole folder is ready to push to GitHub and deploy on Cloudflare Pages —
no build step, no dependencies. It's plain HTML/CSS/JS.

## 1. Push this to GitHub

If you don't already have a repo for this:

```
cd sim-library          # this folder
git init
git add .
git commit -m "Initial sim library site"
```

Then on github.com: click **New repository**, name it something like
`sim-library`, leave it empty (no README/gitignore), and create it. GitHub
will show you a remote URL — run:

```
git remote add origin https://github.com/<your-username>/sim-library.git
git branch -M main
git push -u origin main
```

(If you'd rather use GitHub Desktop or the `gh` CLI, that works too — this is
just a normal git repo.)

## 2. Connect it to Cloudflare Pages

1. Log in to the [Cloudflare dashboard](https://dash.cloudflare.com).
2. Go to **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
3. Authorize Cloudflare to see your GitHub account (if you haven't already)
   and pick the `sim-library` repo.
4. Build settings: this is a static site with no build step, so:
   - **Build command**: leave blank
   - **Build output directory**: `/` (the repo root)
5. Click **Save and Deploy**. Cloudflare will give you a URL like
   `sim-library-abc.pages.dev` within a minute or two.
6. Optional: in the Pages project's **Custom domains** tab, you can rename
   the project or attach a nicer subdomain later, the same way you did for
   `physical-science-8.pages.dev`.

From then on, any `git push` to `main` automatically redeploys the site —
same workflow as your textbook site.

## Updating a simulation later

Each simulation is a single self-contained `index.html` file in its own
folder — open it, edit it, commit, push. No shared assets to break.

## Adding a new simulation later

1. Create a new folder at the repo root (folder name becomes the URL slug,
   e.g. `new-sim-name/`).
2. Put that simulation's `index.html` inside it.
3. Add a link to it in the root `index.html`, inside the right unit/topic
   section (look for the `<div class="sim-grid">` under the topic it
   belongs to, and copy an existing `<a class="sim-card">` block).
