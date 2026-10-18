# Portfolio — Syed Tashriful Alam

Personal portfolio site. Plain HTML, CSS and JavaScript — no build step, no dependencies.

**Live:** _not deployed yet_

## Structure

```
portfolio/
├── index.html          # all markup — the whole site is one page
├── css/styles.css      # design tokens (dark + light), layout, components
├── js/main.js          # split-word headings, scroll reveal, theme toggle
├── assets/
│   ├── me.jpg          # profile photo (800px wide)
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
| Headline, intro, photo stickers | `<header class="hero">` |
| Bio, stats, toolkit, education | `<section id="about">` — the `.bento` tiles |
| Featured projects | `<section id="work">` — one `<article class="feature">` each |
| Smaller projects | `.list` inside `#work` — one `<div class="row">` each |
| Research projects | `<section id="research">` |
| Experience, education | `<section id="journey">` |
| Email, socials | `<footer id="contact">` |

### Colours and type

All colours are CSS custom properties at the top of `css/styles.css`. `:root` holds the
light (cream / navy) palette, `[data-theme="dark"]` overrides it for dark mode. Change
`--accent` to reskin every highlight. Headings mix Inter Tight with *Instrument Serif*
italics — wrap a phrase in `<em>` to get the serif accent.

### Adding a project

For a smaller project, copy a `.row` in the list:

```html
<div class="row rv">
  <span class="r-no">08</span>
  <div class="r-title"><h4>Project name</h4><span>Category &middot; context</span></div>
  <p class="r-desc">What it does and what you built.</p>
  <span class="r-go">&#8599;</span>
</div>
```

A featured project is an `<article class="feature">`: copy one whole, including its
`.f-stage` illustration. Even-numbered features flip the image to the left automatically.

`--d` on any `.rv` element delays its reveal animation — bump it by `.08s` per item.

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
