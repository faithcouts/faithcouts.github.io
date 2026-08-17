# Faith Ann Couts — Personal Academic Website

A static, single-page academic website: HTML + CSS only, no build step, no JavaScript
frameworks.

## Project structure

```
Website/
├── index.html                  # all page content/sections
├── style.css                   # all styling
├── images/
│   └── faith_couts_headshot.jpg
├── files/
│   └── faith-couts-cv.pdf      # linked from the "Download CV" buttons
└── README.md
```

To update content, edit the text directly inside `index.html` — each section is marked
with an HTML comment (`<!-- RESEARCH INTERESTS -->`, etc.). To swap the headshot or CV,
replace the files in `images/` or `files/` with a new file of the **same name**, or update
the `src`/`href` in `index.html` if you rename them.

## Preview locally

From the project folder, run a simple local server (works with Python already installed
on macOS):

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000` in a browser. (Opening `index.html` directly by
double-clicking also works, but a local server more closely matches how GitHub Pages
serves the site.)

---

## Part 1 — Deploy for free on GitHub Pages (`*.github.io`)

### Option A — GitHub Desktop (recommended, no terminal)

1. **Create a GitHub account** if you don't have one already: https://github.com/signup

2. **Create a new repository** at https://github.com/new, named **exactly**
   `<your-username>.github.io` (your GitHub username plus `.github.io` — e.g.
   `faithcouts.github.io`). This exact name is what makes it auto-publish at the clean
   `https://<your-username>.github.io` URL. Leave it public, and don't initialize it with
   a README (you already have one here).

3. **Install GitHub Desktop**: https://desktop.github.com — install it, open it, and
   click **Sign in to GitHub.com** (signs in through your browser, no passwords or tokens
   to copy).

4. **Add this project as a repository**: **File → Add Local Repository**, select this
   project folder. GitHub Desktop will say it isn't a Git repository yet and offer to
   **create a repository** here — click that.

5. **Commit the files**: all the site files will show up under "Changes." Type a summary
   like `Initial website` and click **Commit to main**.

6. **Point it at your GitHub repo**: **Repository → Repository Settings → Remote**, set
   the remote URL to `https://github.com/<your-username>/<your-username>.github.io.git`,
   and **Save**.

7. **Push it up**: click **Push origin** in the top toolbar.

8. **Turn on GitHub Pages**: on the GitHub website, go to **Settings → Pages**, set
   **Source** to **Deploy from a branch**, **Branch** to `main`, folder `/ (root)`, then
   **Save**.

9. **Wait a minute or two**, then visit `https://<your-username>.github.io`. GitHub also
   shows the live URL at the top of the Pages settings once it's deployed.

From now on, whenever you edit files locally, GitHub Desktop will show the changes —
write a summary, **Commit to main**, then **Push origin** to redeploy (live again within
a minute or two).

### Option B — Command line (if you're comfortable with a terminal)

From this project folder:

```bash
git init
git add .
git commit -m "Initial website"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

Then do steps 8–9 above to turn on Pages.

---

## Part 2 — Connect a custom domain later (e.g. `faithanncouts.com`)

If you purchase `faithanncouts.com` (or any domain), here's how to point it at your
GitHub Pages site. None of this needs a terminal or GitHub Desktop — it's all done on the
GitHub website and your domain registrar's website, once Part 1 above is complete and the
site is already live at `https://<your-username>.github.io`.

1. **Buy the domain** from any registrar (Namecheap, Google Domains/Squarespace,
   Cloudflare, GoDaddy, etc.).

2. **Type the domain into GitHub Pages settings.** On the GitHub website, go to your
   repo's **Settings → Pages**, and under **Custom domain**, enter `faithanncouts.com`,
   then **Save**. GitHub automatically adds a `CNAME` file to your repository for you —
   no local file editing needed.

3. **Configure DNS at your registrar.** For an apex/root domain (`faithanncouts.com`,
   no `www`), add these four **A records** pointing `@` to GitHub's IP addresses:

   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

   If you also want `www.faithanncouts.com` to work, add a **CNAME record**:

   ```
   www  →  <your-username>.github.io
   ```

   (Exact steps vary slightly by registrar — look for "DNS settings" or "Manage DNS.")

4. **Wait for DNS to propagate** (a few minutes to ~24 hours), then go back to
   **Settings → Pages** — GitHub will show a green checkmark once it verifies the DNS.
   Check **Enforce HTTPS** so the site serves over `https://`.

5. Your site is now live at `https://faithanncouts.com`, and
   `https://<your-username>.github.io` will continue to redirect to it.

### Notes

- The CV PDF filename in this repo (`Faith Ann Couts_Curriculum Vitae_08.17.26.docx`/`.pdf`
  in the project root) is not the one linked on the site — `files/faith-couts-cv.pdf` is a
  copy of the PDF used for the "Download CV" buttons. Replace `files/faith-couts-cv.pdf`
  whenever you have an updated CV, keeping the same filename so the links keep working.
- The current CV's header says "(January 2026)" even though the file is dated 08.17.26 —
  worth regenerating a corrected PDF before publishing.
