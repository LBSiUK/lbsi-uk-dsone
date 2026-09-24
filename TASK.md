# Instructions for Claude Code

1. Read `HANDOFF.md` fully, then open `design/Portfolio.dc.html` in a browser as the visual reference.
2. Build the site as plain static files at the repo root — no framework, no build step:
   - `index.html`, `styles.css`, `script.js`
   - `assets/Roman.otf`, `assets/images/*` (copy from `design/`)
   One `index.html` with the five views (Home, About, Projects, Blogs, Contact) switched by JS is fine; hash routing (`#about`, `#blog/new-site`) is preferred so views are linkable.
3. Match the design exactly (colours, type, borders, sweep animations) per `HANDOFF.md`.
4. Keep `design/` in the repo as the reference (or delete it if you prefer a clean repo — ask the owner).
5. Create a **public** GitHub repo named **lbsi-uk-dsone** with this description:
   > Introducing the NEW look of my personal website lbsi.uk. There’s a bit of influence from my previous sites here and there but for the most part it’s basically all new. This is meant to somewhat be a showcase of my abilities and as a playground for me to add new stuff and experiment, so this’ll change a lot here and there, or not at all.

   e.g. `gh repo create lbsi-uk-dsone --public --description "<text above>" --source . --push`
   (GitHub caps descriptions at 350 characters — if rejected, keep the full text in README.md and shorten the repo description to its first sentence.)
6. `git init`, commit, push to `main`.
