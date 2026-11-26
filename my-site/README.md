# Conference website

Plain HTML and CSS. No frameworks, no build step.

```
my-site/
├── index.html   all page content (agenda, speakers, venue/map)
├── styles.css   all styling; colours are set at the top
├── .nojekyll    tells GitHub Pages to serve files as they are
└── README.md
```

## Preview locally

Open `index.html` in a browser.

## Edit the content

Everything is in `index.html`, in clearly marked sections:

- **Agenda**: each session is one `<li>` inside `<ol class="schedule">`. Add `class="keynote"` to highlight a slot.
- **Speakers**: each speaker is one `<li class="speaker">`. To use a photo, add it to an `images/` folder and replace the `<div class="avatar">` line with `<img class="avatar" src="images/name.jpg" alt="">`.
- **Map**: the `<iframe>` is an OpenStreetMap embed (no API key needed). To move it, go to openstreetmap.org, find the venue, choose **Share → HTML**, and paste the new `src` in place of the old one.
- **Colours**: change `--color-primary` and `--color-accent` at the top of `styles.css`.

## Deploy to GitHub Pages

Deployment is automatic via `.github/workflows/deploy.yml`, which publishes the `my-site/` folder on every push to `main`.

Repository layout expected by the workflow:

```
<repository root>/
├── .github/workflows/deploy.yml
└── my-site/
    ├── index.html
    └── styles.css
```

One-time setup: in the repository go to **Settings → Pages → Build and deployment** and set **Source** to **GitHub Actions**. After that, every push to `main` redeploys the site to `https://<username>.github.io/<repository-name>/`.
