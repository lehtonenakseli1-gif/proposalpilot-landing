# ProposalPilot — landing page

Static marketing site. No build step, no dependencies to install.
Plain HTML + CSS + vanilla JS; the only external services are Google Fonts (Inter)
and Formspree (contact form).

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The landing page: nav, hero, stats, how it works, features, pricing, contact form, FAQ, CTA, footer |
| `styles.css` | All styling, mobile-first with breakpoints at 700px and 960px |
| `privacy.html` | Privacy policy |
| `terms.html` | Terms of service |

## Run it locally

```bash
python3 -m http.server 4321 --directory .
```

Then open http://localhost:4321.

## Contact form

Every CTA on the page (nav, hero, pricing card, bottom CTA) points at `#contact`.
There is one form and one conversion path.

The form posts to Formspree endpoint `https://formspree.io/f/mgawpjbw` via `fetch`,
so the page never reloads. Submissions arrive in the Formspree dashboard and by email.
To change the endpoint, edit the `action` attribute on `#contactForm` in `index.html`.

Fields sent: `name`, `email`, `business`, `details`, plus a hidden `plan` field that
records which button the visitor clicked (set from each CTA's `data-plan` attribute),
so leads are attributable. `_gotcha` is Formspree's honeypot — bots fill it, people
don't, and Formspree drops those submissions.

## Pricing

$99/month, 3-month minimum, no setup fee. The price appears in three places in
`index.html`: the hero button, the pricing card, and the FAQ. `terms.html` states the
fee and the minimum term. Change all of them together.

## Deploy to GitHub Pages

```bash
gh repo create proposalpilot-landing --public --source=. --push
```

Then in the repo: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`**.
The site goes live at `https://<username>.github.io/proposalpilot-landing/` in a minute or two.
