# Eva’s Vision — development context

## Project and editing

This is the exported source of Eva’s Vision, a bilingual Czech/English AI creator portfolio. The owner communicates in Russian. Work directly on this existing static site and preserve its current design unless the owner requests a redesign.

There is no framework, build pipeline, backend, dependency install or database. The deployable site is the repository root (GitHub Pages). The authoritative source is `index.html`: embedded CSS, HTML, Czech/English `copy` dictionaries and vanilla JavaScript. `fonts.css` and `assets/` are local assets. Serve with `python3 -m http.server 8000` from the project root.

Read `index.html` before editing. New translations are added with `Object.assign(copy.cs, ...)` and `Object.assign(copy.en, ...)` before `setLanguage`. `data-t` binds translated content, `data-alt` binds image descriptions. Keep every referenced key present in both languages. Language preference uses localStorage.

## Brand

- Eva’s Vision, Prague; Instagram: https://www.instagram.com/evas_vision/ (current site contact).
- Minimal editorial aesthetic with cream #fbf5ef, chocolate #51372d, blush #bd8e83 and line #d9c9bd.
- Headings: Instrument Serif. Body: Manrope. Fonts are served locally.
- Realistic blush-cosmos flower asset for rounded call-to-action buttons and click particles.
- Preserve responsive layouts, keyboard focus styles, lazy loading and prefers-reduced-motion behavior.

## Existing functionality

Header navigation; CZ/EN toggle; category filtering; services; pricing; about; collaboration process; Instagram contact; AI transparency; footer. Gallery cards link to native details elements. Lightbox is a native dialog with project-scoped previous/next navigation, keyboard arrows, Escape, close button and scroll restoration. Image links fall back to opening the full-resolution image if the lightbox is unavailable.

Two gallery projects exist:

1. `clay-court-summer` (Fashion): Clay Court Summer, independently conceived AI editorial inspired by Alo Yoga, made with Nano Banana. Description from the owner's supplied info.md. Cover is the portrait with a tennis racket, then fabric close-up and playful overhead shot. All 3 photos are included.
2. `soft-structure` (Product and Fashion): cream bag with chocolate-brown tailoring. Soft Structure is a working title assigned during upload; no brand or tool has been confirmed. Cover is the portrait in the mountain landscape, then product in motion and overhead view on stone steps. All 3 photos are included.

`data-category` can contain multiple space-separated categories. Keep filtering compatible with this. Video is a placeholder awaiting footage.

## Pricing (Kč)

Individual services: associative photo 450; hero/model photo 750; video up to 15 s 1,850; up to 30 s 2,750; up to 60 s 3,900; carousel of up to 5 slides 850.

Monthly packages:

| Package | Price | Contents | Individual total | Saving |
| --- | ---: | --- | ---: | ---: |
| ZÁKLAD | 6,200 | 10 associative photos + 2 hero/model photos + 1 carousel | 6,850 | 650 (9.5%) |
| FOTO | 7,300 | 12 associative photos + 4 hero/model photos | 8,400 | 1,100 (13.1%) |
| VIDEO | 7,900 | 2 videos up to 15 s + 2 videos up to 30 s | 9,200 | 1,300 (14.1%) |
| VÝHODA | 12,000 | 15 associative photos + 4 hero/model photos + 1 video up to 30 s + 2 carousels | 14,200 | 2,200 (15.5%) |
| VIZE | 21,000 | 28 associative photos + 6 hero/model photos + 2 videos up to 30 s + 3 carousels | 25,150 | 4,150 (16.5%) |

VÝHODA is visually recommended. Preserve these prices and quantities unless the owner asks for changes. Existing terms: two rounds of minor revisions per deliverable; additional photo revisions 180 Kč/item, video 400 Kč/item; extras at individual rates; final scope, price and timing confirmed after consultation. Carousel is design/sequence/short copy using finished photos, not five additional photo generations.

## Content constraints

The owner wants AI disclosure and independent concepts presented accurately. Preserve current AI labels and AI & Transparency copy. Do not imply that the featured brands commissioned, sponsored or endorsed the concepts. Do not invent client names, client relationships, outcomes, testimonials, portfolio tools or creator achievements. Preserve supplied images and their proportions.

## Validation and publication

For edits, check JavaScript syntax, both language dictionaries including alt-text, local asset paths, anchor targets and changed behavior. For visual/layout work, check mobile and desktop in a browser when available. No browser visual QA was performed before this export.

This export has no original Git history, hosting configuration or credentials. It does not automatically update the existing hosted site. Keep changes local until the owner requests deployment through an available hosting workflow.

GitHub Pages: the repository `evasvision/evasvision.github.io` is published by GitHub Pages directly from the root of `main` (Deploy from a branch; `.nojekyll` disables Jekyll). The original export kept the site in `dist/`; it was moved to the root for Pages. EXPORT.json paths still use the `dist/` prefix. All asset paths are relative, so the site works from the domain root. Note: the initial GitHub upload flattened files and lost the four Clay Court Summer images whose names collide with Soft Structure (`portrait`, `portrait-small`, `overhead`, `overhead-small` .webp); they must be re-uploaded to `assets/clay-court-summer/` (checksums in EXPORT.json).
