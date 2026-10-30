# XE 54 Intelligence Solutions website

A responsive static website built with HTML, CSS and browser-native JavaScript modules. There is no framework, build step, dependency install or external CDN.

## Run the site

- Open `index.html` in a current browser. The page uses native ES modules; if the browser restricts modules or local assets under `file://`, use VS Code Live Server or another local static HTTP server.
- With VS Code Live Server installed, open `index.html` and choose **Open with Live Server**.
- No credentials, API keys or client information are needed. The Client Portal is a labelled front-end demo, not an authentication system.

## Replace the image placeholders

The site currently contains no third-party photographs. Each image area shows a navy-to-gold gradient and inline SVG until a photo is supplied.

1. Review [assets/img/README.md](./assets/img/README.md) for the ten requested filenames, target sizes, subject guidance and credit requirements.
2. Add each approved photograph in WebP format and a same-basename JPG fallback under `assets/img/`. Keep each file below 250 KB and at the specified dimensions.
3. Record the original source, author, licence and attribution in `assets/img/README.md`. Do not use unlicensed photos, identifiable faces without releases, real military insignia or third-party logos.
4. Update the image filename, dimensions and descriptive alt text in `assets/js/ui.js` or `assets/js/data.js`, depending on the image.
5. Check the page with both image formats present and with the image files removed; the latter should display the gradient and SVG placeholder.

## Edit content and interactions

- **`assets/js/data.js`** — navigation, divisions, products and readiness, roadmap phases, financial values, courses, safeguards, accreditation status and image filenames.
- **`assets/js/ui.js`** — page markup, navigation groups, image markup, text, labels and accessible component structure.
- **`assets/js/charts.js`** — the investor chart's SVG drawing, metric display and tooltips.
- **`assets/js/app.js`** — routing, theme, menu, filtering, tabs, dialogs, form validation, interactions and `FORM_ENDPOINT`.
- **`styles.css`** — colours, responsive layout, typography, dark mode and reduced-motion presentation.
- **`index.html`** — page metadata, Organization JSON-LD, global landmarks and shared dialog markup.

Product readiness is deliberately limited to the stated stages: Skua prototype, Peregrine integrating, ActiveEye deployed, UIP alpha and counter-drone lab prototype. Accreditation rows are stated as in preparation; update them only when the status is verified.

The contact form validates in the browser and collects name, email, optional company name, enquiry type and message. `FORM_ENDPOINT` in `assets/js/app.js` is empty until a real secure endpoint is supplied. With no endpoint configured, the page provides a `mailto:` link with no recipient address, so the user can choose and address the message. Configure a real same-origin endpoint before treating submissions as operational.

## SEO and deployment (Webway)

1. Upload everything into the domain's document root (usually `public_html`). The homepage file must be named exactly `index.html` (not `index.html.html`); turn on "show file extensions" if unsure.
2. Upload the whole `assets/` folder with its structure intact: `assets/logo.svg`, `assets/js/app.js`, `ui.js`, `data.js`, `charts.js` and `assets/img/`. Without it the page loads as an empty shell.
3. Make both `xe54intelligence.co.za` and `www.xe54intelligence.co.za` resolve, and redirect one to the other. The canonical domain used in `index.html`, `sitemap.xml` and `robots.txt` is `https://www.xe54intelligence.co.za/`.
4. Set `FORM_ENDPOINT` in `assets/js/app.js` to the backend URL. The form should post there first and fall back to `mailto:` if the request fails.
5. When a publishable PNG or JPG share image exists, point `og:image` at it (many social platforms do not render SVG previews).
6. After deploying, check `/robots.txt` and `/sitemap.xml` load, then submit the sitemap in Google Search Console.

## Manual smoke test

1. Open the home page and check the animated headline, counters and all four division summaries.
2. Resize to 320px wide and desktop size; verify that navigation and content do not scroll horizontally.
3. Open Catalogue, filter by category, search, open a product detail, press Escape, and try **Request a quote**.
4. Check Division tabs with Tab, arrow keys, Home and End. Test Roadmap phases with arrow keys and buttons.
5. Switch the financial metric and focus or hover chart points. Check that the logistics panel and portal show demo labels.
6. Filter Academy courses and expand Responsible AI cards. Submit the contact form empty and verify inline errors; complete it and inspect the email fallback link.
7. Switch themes, reload, and verify the choice persists. Enable reduced motion in the operating system or browser and verify the page remains usable.
