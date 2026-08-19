# ProposalPilot — landing page

Static marketing site. No build step, no dependencies to install.
Plain HTML + CSS + vanilla JS; the only external services are Google Fonts (Inter)
and Formspree (waitlist form).

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The landing page: nav, hero, stats, how it works, features, pricing, waitlist, FAQ, CTA, footer |
| `styles.css` | All styling, mobile-first with breakpoints at 700px and 960px |
| `privacy.html` | Privacy policy |
| `terms.html` | Terms of service |

## Run it locally

```bash
python3 -m http.server 4321 --directory .
```

Then open http://localhost:4321.

## Waitlist form

The form posts to Formspree endpoint `https://formspree.io/f/mgawpjbw` via `fetch`,
so the page never reloads. Submissions arrive in the Formspree dashboard and by email.
To change the endpoint, edit the `action` attribute on `#waitlistForm` in `index.html`.

## Pricing buttons

Both "Get started" buttons are `mailto:` links to lehtonen.akseli1@gmail.com with a
prefilled subject. To switch to Stripe, replace the two `href` values in the pricing
section with your Stripe Payment Link URLs.

## Deploy to GitHub Pages

```bash
gh repo create proposalpilot-landing --public --source=. --push
```

Then in the repo: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`**.
The site goes live at `https://<username>.github.io/proposalpilot-landing/` in a minute or two.
