# Pro Fit Doors

Production-oriented, five-page static marketing website for Pro Fit Doors, Edmonton. Built with semantic HTML, responsive CSS and vanilla JS. Original project photos supplied by client. No JS framework or build dependency required for deployment.

## Pages
- `/` — Home
- `/services/` — Door installation and replacement services
- `/our-work/` — Photo gallery / accessible lightbox
- `/about/` — About and service approach
- `/contact/` — Free estimate request

## Cloudflare Pages deployment

Connect this repository to Cloudflare Pages using the **main** branch. For the static site, leave the build command blank and set the output directory to `/` (repository root). The `functions/api/contact.js` Pages Function handles form submissions on the same deployment.

**Contact form setup (required before accepting enquiries):**

1. In Cloudflare Turnstile, create a widget for the actual site domain. Copy its **site key** into `config.js` as `turnstileSiteKey`. If you use a preview domain, register it as appropriate.
2. In Cloudflare Pages → Settings → Variables and Secrets, add:
   - `TURNSTILE_SECRET_KEY` — corresponding Turnstile secret (encrypt it)
   - `RESEND_API_KEY` — Resend API key (encrypt it)
   - `CONTACT_TO_EMAIL` — desired inbox, initially `itsme@anthonymeszaros.com`
   - `CONTACT_FROM_EMAIL` — verified sender, initially `emails@rtuino.com`
3. Redeploy after setting environment variables. Confirm Resend's sending domain is verified.
4. Submit a test enquiry and confirm delivery. The form intentionally remains disabled if the public site key is empty; **do not consider it operational until configured and tested**.

**Important:** the form sends inquiries to the configured recipient, not automatically to the client's phone number. Decide on the final recipient with the client before going live. All phone and SMS links point to the number in their Kijiji ad.

## Local preview

Use a static HTTP server rooted in the project directory to preview all routes. The form requires a live Cloudflare Pages Functions environment to work and will not deliver from a plain local file server. `node generate.js` regenerates the HTML from `site.js` if you make shared template changes; generated HTML is already included, so no build command is needed in production.

## Before launch

- Verify all claims, service coverage, photo permissions and business name with the client.
- Confirm final contact form delivery address.
- Configure Turnstile + Resend and test form on live deployment.
- Set a production domain and add canonical/OG URL metadata, update sitemap when the domain is known.
- Check AODA/accessibility, browser and device behavior using real hardware.

No invented testimonials, business address, years of operation, warranty, prices or business hours were added.
