# So Go Airsoft — Demo Redesign

A proposed redesign of [sogoairsoft.com](https://www.sogoairsoft.com/), built as a static site so it costs nothing to host and is trivial to hand off.

## What this is

- 7 pages: home, play (Ozark indoor), rock (Bolivar outdoor), parties, pricing, shop, contact
- Fully responsive (mobile-first)
- No build step, no JavaScript framework, no database
- All content sourced from publicly available info (current sogoairsoft.com, Yelp, Groupon, BBB, Springfield Business Journal, Facebook)
- Tailwind via CDN, Google Fonts (Anton + Inter)
- A single embedded Google Map on `/contact.html`
- "DEMO PREVIEW" banner across the top of every page so anyone landing on the link knows what they're looking at

## Stack

| | |
|---|---|
| HTML | Hand-written, semantic |
| CSS | Tailwind (CDN) + 30 lines of `styles.css` |
| JS | ~6 lines for the mobile menu and copyright year |
| Hosting | GitHub Pages (free, unlimited bandwidth for public sites) |

## Run locally

```bash
cd sogo-airsoft-demo
python3 -m http.server 8080
# open http://localhost:8080
```

## File map

```
sogo-airsoft-demo/
├── index.html          # Home — hero, activity tiles, two-locations split, schedule preview, hours
├── play.html           # Ozark CQB: block play schedule, game types, rules, what to bring
├── rock.html           # The Rock: outdoor 80-acre quarry in Bolivar — terrain, FPS tiers, events
├── parties.html        # Private parties (Nerf, Gel, Airsoft, Paint), FAQ
├── pricing.html        # Block play, open play, rentals, party rates
├── shop.html           # Retail categories + tech services
├── contact.html        # Address, hours, embedded map, directions
├── 404.html            # Custom not-found page
├── styles.css          # ~30 lines of supplemental CSS
├── robots.txt
├── sitemap.xml
├── .nojekyll           # Tell GitHub Pages to skip Jekyll processing
└── README.md           # this file
```

## Customizing for the owner

The site is plain HTML — anyone with Notepad/VSCode and 5 minutes can edit it.

**To swap colors site-wide**, edit the `tailwind.config` block in each `<head>`:

```js
colors: {
  ink:   '#0a0a0a',  // dark backgrounds
  flame: '#f97316',  // primary accent (orange)
  ember: '#fb923c',  // hover state
}
```

**To remove the demo banner** before going live, delete this block from each page (top of `<body>`):

```html
<div class="bg-flame text-black ...">DEMO PREVIEW · ...</div>
```

**To add real photos**, drop them into a new `images/` folder and replace any of the gradient hero sections with `<img>` tags. The hero structure is set up to layer an image behind the existing gradient overlay easily.

## Source content

All copy and business details were pulled from publicly available sources:

- [sogoairsoft.com](https://www.sogoairsoft.com/) — current site (services, rules, hours)
- [Yelp](https://www.yelp.com/biz/so-go-airsoft-ozark) — verified address and hours
- [Groupon](https://www.groupon.com/biz/ozark-mo/so-go-airsoft) — 4.9★ rating, 100+ reviews
- [BBB](https://www.bbb.org/us/mo/ozark/profile/paintball-games/so-go-airsoft-0734-30541) — owner name (Jon Burdette)
- [Springfield Business Journal](https://sbj.net/stories/so-go-airsoft,837) — founding year (2007)
- [Facebook page](https://www.facebook.com/p/So-Go-Airsoft-100063692404826/) — community presence

## Transferring to the owner

If the owner wants to take this over:

1. Repo can be transferred to their GitHub account in one click (Settings → Transfer ownership).
2. They can point a custom domain (e.g., `sogoairsoft.com`) at GitHub Pages — see GitHub's [custom domain guide](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).
3. Or they can download the repo as a ZIP and host it anywhere — Netlify, Cloudflare Pages, even a $5/mo shared host. It's just static files.
