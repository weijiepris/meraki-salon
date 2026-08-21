# Meraki Hair Salon — static site

A single-page rebuild of merakisalonsg.com. No build step, no dependencies.

## Files

- `index.html` — the whole site (HTML + CSS + JS inline)
- `assets/` — 51 images pulled from the current site
- `meraki-preview.html` — a self-contained copy with every image base64-inlined.
  Only used for the shareable preview link; do **not** deploy this one (8 MB).

## Preview locally

Open `index.html` in a browser, or serve the folder:

    npx serve .

## Deploy

Upload `index.html` + the `assets/` folder to any static host (Netlify drop,
Cloudflare Pages, GitHub Pages, or your existing hosting's public_html).
Nothing else is required — the only external request is Google Fonts.

## Editing content

Everything lives in `index.html`:

| What | Where |
| --- | --- |
| Promotions and prices | `<section id="promos">` |
| Signature services | `<section id="signature">` |
| Full service menu | `<section id="services">` |
| Gallery | the `CATS` array in the script at the bottom — images are `assets/<PREFIX>_1..5.jpg` |
| Team | `<section id="team">` |
| Reviews | the `REVIEWS` array in the script at the bottom |
| FAQ | `<section id="faq">` |
| Address, hours, contact | `<section id="visit">`, the footer, and the JSON-LD block |

Booking links all point to `https://wa.link/3koy9r`. Search for that string to
change every CTA at once.

## Adding gallery photos

Drop a file into `assets/` named `<PREFIX>_<n>.jpg` (e.g. `HC_6.jpg`) and raise
the loop bound in the script:

    for(var i = 1; i <= 5; i++){

Prefixes: `HairTrans_`, `NBC_`, `GHB_`, `AFT_`, `LSP_`, `HC_`.

## Notes

- Prices shown are the August promotions scraped from the live site. Update the
  `<section id="promos">` block when they change, and the "August Hair Deals"
  label with it.
- Reviews are verbatim 5-star Google reviews from the current site's Trustindex
  widget, with emoji and HTML entities normalised to plain text.
- The `assets/Kevin-Photo.jpg` file is Calvin's photo — that filename comes from
  the original site.
