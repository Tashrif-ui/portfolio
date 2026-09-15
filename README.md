# Portfolio — Syed Tashriful Alam

Personal portfolio site. Plain HTML, CSS and JavaScript — no build step, no dependencies.

**Live:** _not deployed yet_

## Structure

```
portfolio/
├── index.html          # all markup — the whole site is one page
├── css/styles.css      # design tokens (dark + light), layout, components
├── js/main.js          # theme toggle, scroll reveal, counters, mobile menu
├── assets/
│   ├── me.png          # profile photo
│   └── Syed_Tashriful_Alam_CV.pdf
└── vercel.json         # clean URLs, cache + security headers
```

## Running locally

Any static server works. With Node installed:

```bash
npx serve .
```

Then open the URL it prints. Opening `index.html` directly works too.

## Editing content

Everything lives in `index.html` — there is no CMS or data file to look up.

| What | Where |
|---|---|
| Name, role, intro | `<section class="hero">` |
| Bio, education, facts | `<section id="about">` |
| Tech chips | `.stack-card` inside `#about` |
| Projects | `<section id="work">` — one `<article class="card">` each |
| Email, socials | `<section id="contact">` |

### Colours

All colours are CSS custom properties at the top of `css/styles.css`. `:root` holds the
dark palette, `[data-theme="light"]` overrides it for light mode. Change `--accent`,
`--accent-2`, `--accent-3` and `--grad` to reskin the whole site.

### Adding a project

Copy an existing `<article class="card">` block and edit it:

```html
<article class="card reveal" style="--d:.06s">
  <div class="card-top">
    <span class="card-icon" aria-hidden="true">&#128640;</span>
    <span class="card-tag">Private client work</span>
  </div>
  <h4 class="card-title">Project name</h4>
  <p class="card-desc">What it does and what you built.</p>
  <ul class="card-tech"><li>Next.js</li><li>React</li></ul>
</article>
```

`--d` staggers the reveal animation — bump it by `.06s` per card.

## Deploying to Vercel

1. Push this repo to GitHub.
2. On [vercel.com](https://vercel.com), **Add New → Project** and import the repo.
3. Framework preset: **Other**. Leave build command and output directory empty —
   it is a static site.
4. Deploy. Every push to `main` redeploys automatically.

## Notes

- **Placeholder links** — any `<a data-needs-url="...">` is hidden by `js/main.js`
  until a real URL is filled in, so nothing ships broken. Remove the attribute once
  the `href` is set.
- **Client projects** are described without repo names or links, since those
  repositories are private client work.
- **Contribution graph** comes from `ghchart.rshah.org`. It only counts private
  contributions if *Settings → Profile → Include private contributions on my profile*
  is enabled on GitHub.
