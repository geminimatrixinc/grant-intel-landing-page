# Ohahase — holding page

A single self-contained holding page for **ohahase.ca**, served while the product itself
(private beta) finishes its production deploy.

`index.html` is the whole thing: **no build step, no dependencies, no JavaScript.** The only
external link on the page is to [geminimatrixinc.com](https://geminimatrixinc.com/). It can be
dropped onto any host as-is.

## Why it exists

Outreach letters to Indigenous organisations (OFNTSC, FNESL, CCIB and others) name Ohahase
directly. Until this page existed, `ohahase.ca` served a GoDaddy parked-domain lander with
unrelated ads — so anyone who received a letter and looked the name up found ad spam. This
replaces that with something honest and on-brand.

Its primary audience is therefore **the organisations being asked for RFP listing permission**,
not suppliers. The "If we've written to you about your RFPs" section restates the ask exactly as
the letters put it: title, closing date, link back, no documents reproduced.

## Design

Uses the same brand tokens as the Ohahase app (`web/app/tailwind.config.ts`, `app/globals.css`
in the main repo), so this page and the launched site do not read as two different products:

| Token | Light | Dark |
|---|---|---|
| Accent (`pine`) | `#4f46e5` | `#818cf8` |
| Surface | `#ffffff` | `#111827` |
| Page background | `#ffffff` | `#0b1120` |
| Primary text | `#0f172a` | `#f1f5f9` |
| Border | `#e2e8f0` | `#2a3441` |

Light by default, with `prefers-color-scheme: dark` support. Responsive down to 360px.

## Deploying

**Static host (Hostinger, etc.)** — upload `index.html` to the web root, then point the
`ohahase.ca` **A record** at the host.

> ⚠️ **A record only — leave the nameservers at GoDaddy.** Moving nameservers means recreating
> every Resend SPF/DKIM record, which would break transactional email.

**GitHub Pages** — enable Pages on `main` in repo settings, then add a `CNAME` file containing
`ohahase.ca` and point DNS at GitHub's IPs. Not set up here, so that choice stays open.

## Retiring it

This page comes down when the app itself deploys to `ohahase.ca`
(`work/todo/launch/` — A1 in `ROAD-TO-2026-11-01.md`). Content worth keeping at that point:
the permission-first section has no equivalent on the current site, and it is the thing source
organisations actually need to read.

## Contact

`geminimatrixinc@gmail.com` — deliberately, not `hello@ohahase.ca`. Resend is configured to
*send* from the domain; that does not mean a mailbox there *receives*. Swap it once a real
mailbox is confirmed.
