---
name: website-starter
description: Start a new static (GitHub Pages) website from the Slothie template - bilingual DE/EN legal pages (Impressum, Datenschutz) with placeholders, Lucide icon license, a reference homepage design, and an accessibility/launch checklist. Use when creating a new homepage or when asked to set up legal pages for a site.
---

# Website Starter

Sets up a new static, cookie-free, bilingual (DE/EN) homepage based on the Slothie site. Assets live in `assets/`.

## Workflow

1. **Collect data** (ask the user, one question at a time, only what is missing): name or company, street, postal code and city, email, domain, brand name, email provider (name, address), domain registrar (name, address), competent data protection authority (name, address, URL), hosting provider (default GitHub Pages), optional notice for the legal page (e.g. app status, trademark note), date.
2. **Copy** into the project root: `assets/impressum.html`, `assets/datenschutz.html`, `assets/legal.css`, `assets/LUCIDE-LICENSE.txt`. Ask for `logo.png`; create `CNAME` (domain) and an empty `.nojekyll`.
3. **Fill placeholders**: replace every `{{...}}`, then verify none remain (`grep -rn "{{" .`). Delete the optional section 7 in `datenschutz.html` (DE and EN, plus the HTML comments) and renumber, or fill it for every additional service.
4. **Build the homepage**: use `assets/index.reference.html` only as structural reference (single file, inline CSS/JS, `data-i18n` translations, skip link, language switch without storage). Write new content, palette and layout for the new brief following the `frontend-design` skill. Do not copy Slothie texts, colors or imagery.
5. **Icons**: use Lucide icons as inline SVG only. Keep `LUCIDE-LICENSE.txt` and a footer link to it. No CDN.
6. **Footer** must link Impressum, Datenschutz and Icon-Lizenz on every page.
7. **Verify** with the `webapp-testing` skill: serve locally, screenshot desktop and mobile, check language switch, console without errors, all links resolve.

## Privacy baseline (must stay true)

The shipped Datenschutz text claims: no cookies, no analytics/tracking, no ads, no third-party embeds, no external fonts or CDNs, no contact form, no local storage. If the new site adds any of these (forms, maps, video, analytics, Google Fonts, newsletter, cookies), update sections 2 and 7 accordingly and add consent where required. Never leave the baseline claims in place when they are false.

## Accessibility checklist (WCAG 2.2 AA, short)

- Semantic landmarks (`header`, `nav`, `main`, `footer`), one `h1`, ordered headings, `lang` set and updated on language switch.
- Text contrast >= 4.5:1, UI components >= 3:1; never meaning by color alone.
- Visible keyboard focus, logical tab order, skip link, all controls reachable by keyboard.
- Alt text for informative images, empty `alt=""` for decorative ones; icon-only buttons have an accessible name.
- Respect `prefers-reduced-motion`; responsive down to 320px without horizontal scroll; text resizable to 200%.
- Unique `<title>` and meta description per page.

## Legal notes

- Impressum per § 5 DDG, content responsibility per § 18 Abs. 2 MStV; companies also need legal form, register, VAT ID.
- Competent authority depends on the controller's residence or seat.
- Texts are a working basis, not legal advice. Tell the user to have them reviewed before publication of a commercial site.
- Update the "Stand" date on every change.

## Assets

| File | Purpose |
|---|---|
| `assets/impressum.html`, `assets/datenschutz.html` | Legal pages DE/EN with `{{PLACEHOLDERS}}` |
| `assets/legal.css` | Styles for legal pages (expects `logo.png`) |
| `assets/LUCIDE-LICENSE.txt` | ISC license for Lucide icons |
| `assets/index.reference.html` | Slothie homepage as design/structure reference |
