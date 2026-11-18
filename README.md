# Harsyntra Website

Marketing site for [www.harsyntra.com](https://www.harsyntra.com) — the public site for
Harsyntra, workforce scheduling, time tracking, and labor cost analysis for hourly teams.

## What is in this repo

- `index.html` — the whole site, one self-contained static file (assets inlined).
- `.github/workflows/deploy.yml` — deploys to the VPS on every push to `main`.

## Deploy

Every push to `main` copies `index.html` to `/var/www/harsyntra-site/` on the VPS,
where nginx serves it as www.harsyntra.com. No build step, nothing to restart.

Required repo secrets (Settings → Secrets and variables → Actions), same values
as the Roster app repos:

- `DEPLOY_HOST` — VPS host (IP)
- `DEPLOY_USER` — SSH user
- `DEPLOY_PASSWORD` — SSH password

One-time server setup (not part of CI): DNS A record `www` → VPS IP, nginx server
block for `www.harsyntra.com` serving `/var/www/harsyntra-site`, and a Let's Encrypt
cert (`certbot --nginx -d www.harsyntra.com -d harsyntra.com`).

## Updating the site

The site is built and previewed in Muse (artifact `harsyntra-marketing-site`).
To update: edit there, export the file, replace `index.html` here, push to `main`.

## Rules for the site

- No plan prices anywhere — pricing is tailored per organization.
- The product story ends at labor cost analysis. Payroll, payslips, and tax &
  deductions are future scope ("on the roadmap"), never promised as available.
- Primary CTA is "Book a demo" (mailto:support@harsyntra.com). Sign in links to
  https://app.harsyntra.com. No public signup form.
