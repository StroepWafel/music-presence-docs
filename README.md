# Music Presence Documentation

This repository contains the documentation for [Discord Music Presence](https://github.com/ungive/discord-music-presence), built with [Zensical](https://zensical.org/).

## Setting up

1. Create and activate a virtual environment, then install Zensical:

   **Windows (Command Prompt or PowerShell):**
   ```bash
   python -m venv .venv
   .venv\Scripts\activate
   pip install zensical
   ```

   **macOS / Linux:**
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   pip install zensical
   ```

2. Preview the site locally:
   ```bash
   zensical serve
   ```
   Open [http://localhost:3000](http://localhost:3000) in your browser. The site reloads when you change files in `docs/`.

Configuration is in `zensical.toml`. Key options include `site_name`, `site_url`, `docs_dir` (source Markdown; default `docs`), and `site_dir` (build output; default `site`). Set `site_url` for instant navigation and correct canonical URLs.

Replace `favicon.png` (or `favicon.ico`) in /docs/images for the site’s browser tab icon. The path is set in `zensical.toml` under `[project.theme]` → `favicon`.



---

## Publishing

### Option 1: GitHub Pages

This repo includes a GitHub Actions workflow (`.github/workflows/docs.yml`) that builds and deploys the site on every push to `main` or `master`.

**To publish:**

1. In your GitHub repo, go to **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.
3. Push to `main` (or `master`). The workflow runs automatically and deploys the built site.

The site will be available at `https://<username>.github.io/<repo-name>/` (or your custom domain if configured).

**Before the first deploy:** Set the real URL in `zensical.toml` so links and metadata are correct:
   ```toml
   site_url = "https://your-username.github.io/music-presence-docs/"
   ```

### Option 2: Build and deploy manually

1. Build the static site:
   ```bash
   zensical build --clean
   ```
   Output is written to the `site/` directory.

2. Upload the contents of `site/` to any static host (e.g. Netlify, Vercel, or your own server). Use the root of `site/` as the site root.

### Option 3: GitLab Pages

For GitLab, set `site_dir = "public"` in `zensical.toml`, then use a `.gitlab-ci.yml` that runs `pip install zensical` and `zensical build --clean`, and publish the `public` directory. See [Zensical: Publish your site](https://zensical.org/docs/publish-your-site/) for a full example.
