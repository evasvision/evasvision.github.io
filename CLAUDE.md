# Eva’s Vision — development context

## Project and editing

This is the exported source of Eva’s Vision, a bilingual Czech/English AI creator portfolio. The owner communicates in Russian. Work directly on this existing static site and preserve its current design unless the owner requests a redesign.

There is no framework, build pipeline, backend, dependency install or database. The deployable site is the repository root (GitHub Pages). The authoritative source is `index.html`: embedded CSS, HTML, Czech/English `copy` dictionaries and vanilla JavaScript. `fonts.css` and `assets/` are local assets. Serve with `python3 -m http.server 8000` from the project root.

Read `index.html` before editing. New translations are added with `Object.assign(copy.cs, ...)` and `Object.assign(copy.en, ...)` before `setLanguage`. `data-t` binds translated content, `data-alt` binds image descriptions. Keep every referenced key present in both languages. Language preference uses localStorage.

## Brand

- Eva’s Vision, Prague; Instagram: https://www.instagram.com/evas_vision/; e-mail evas_vision@seznam.cz (owner asked to show her e-mail; mailto link with a language-specific subject, `data-mail`); IČO 29955084 (contact list and footer).
- Minimal editorial aesthetic with cream #fbf5ef, chocolate #51372d, blush #bd8e83 and line #d9c9bd.
- Headings: Instrument Serif. Body: Manrope. Fonts are served locally.
- Large section titles (h1/h2) have no trailing periods (owner request); mid-title sentence breaks use `<br>`.
- Section intro text (`.heading > p`) sits under the title, not in a right-hand column (the owner found that empty-looking): 17px, max 560px, thin blush left rule with a small ✦.
- Realistic blush-cosmos flower asset for rounded call-to-action buttons and click particles.
- Preserve responsive layouts, keyboard focus styles, lazy loading and prefers-reduced-motion behavior.
- Living background (owner request): a fixed `.ambient` layer behind all content with four slowly drifting blush/cream radial-gradient blobs (CSS keyframes, no `filter: blur` — it dropped software rendering to ~13 fps) and a `#ambient-dust` canvas of rising, twinkling sparkles (≤70) and slowly falling, tumbling blush petals (7–18), DPR capped at 2, frame-rate independent, paused when the tab is hidden. The first version was too subtle for the owner to notice; blobs were made more saturated (opacity .9) and faster (17–28 s loops). Under prefers-reduced-motion the blobs are static and the canvas is hidden.

## Existing functionality

Header navigation; CZ/EN toggle; category filtering; services; pricing; about; collaboration process; Instagram contact; AI transparency; footer. There are no project detail panels (the owner asked to remove them). Each photo project card is an in-card carousel (`.card-carousel` with a scroll-snap `.carousel-track`): swipe on touch, ‹ › buttons and arrow keys, a `1 / n` counter; single-photo projects get no controls. Card text: title, short line and the project meta line (`.card-meta`, includes the brand inspiration). Clicking a slide opens the lightbox, a native dialog with project-scoped previous/next navigation, keyboard arrows, Escape, close button and scroll restoration; it shows the project description and brand disclosure (`data-desc`/`data-disc` on the carousel) below the controls. Slide links fall back to opening the full-resolution image if the lightbox is unavailable. Video cards play a muted preview while visible; the play button swaps in the full file (with sound where the source had audio) and shows native controls in the card (`.video-cover.is-active`, `object-fit:contain`). `.section` uses `overflow:clip` so focus or scrollIntoView inside a carousel can never scroll the section sideways.

Fifteen gallery projects exist:

1. `clay-court-summer` (Fashion): Clay Court Summer, independently conceived AI editorial inspired by Alo Yoga, made with Nano Banana. Description from the owner's supplied info.md. Cover is the portrait with a tennis racket, then fabric close-up and playful overhead shot. All 3 photos are included.
2. `soft-structure` (Product and Fashion): cream bag with chocolate-brown tailoring. Soft Structure is a working title assigned during upload; no brand or tool has been confirmed. Cover is the portrait in the mountain landscape, then product in motion and overhead view on stone steps. All 3 photos are included.

3. `ahoj-europe` (Video and Product & Beauty): 12 s vertical beauty video inspired by rhode, uploaded by the owner. "Ahoj, Europe" is a working title taken from the note in the final shot; no tool has been confirmed. Files in `assets/ahoj-europe/`: `ahoj-europe.mp4` (1080×1920, 30 fps, H.264, no audio — the source audio track was silent) for in-card playback, `ahoj-europe-small.mp4` (720×1280) for the card cover, plus `poster.webp`/`poster-small.webp`. The cover video autoplays muted only while visible and never under prefers-reduced-motion. `data-t-label` binds translated aria-labels.
4. `lime-shot` (Product & Beauty): eye booster series inspired by celimax Retinal Shot, photos supplied by the owner. Lime Shot is a working title assigned during upload; no tool has been confirmed. Cover is the beauty portrait with two tubes, then the street shot (white pumps visible, disclosure also covers other depicted brands), then the tentacle product still life. All 3 photos are included; the street photo is 1120×1500, the others 1493×2000.
5. `daisy-meadow` (Fashion): kidswear editorial in a daisy meadow, photos supplied by the owner. Daisy Meadow is a working title assigned during upload; no brand or tool has been confirmed. Cover is the smiling portrait looking back, then the bouquet with straw hat, then the embroidered cardigan detail. All 3 photos are included (1493×2000).
6. `sky-and-sand` (Product & Beauty): sunscreen series inspired by Beauty of Joseon Relief Sun, photos supplied by the owner. Sky & Sand is a working title assigned during upload; no tool has been confirmed. Cover is the freckled beauty portrait with the tube, then the tube on sand, then the cream texture shot. All 3 photos are included (1493×2000).
7. `honey-drip` (Product & Beauty): hair mask series inspired by Gisou Honey Gloss, photos supplied by the owner. Honey Drip is a working title assigned during upload; no tool has been confirmed. Cover is the jar on ice cream with honey drip, then the jar in a clear bag with honeycomb, then the layered hearts with arrows. All 3 photos are included (1493×2000).
8. `wild-silk` (Video and Fashion): 12 s vertical fashion video, white silk dress on a wild misty coast, uploaded by the owner. Wild Silk is a working title; no brand or tool confirmed. Same video structure as `ahoj-europe`, but the full file keeps the original audio (AAC 128 kbps); the card cover file has no audio.
9. `elegance-v-pohybu` (Video and Fashion): 15 s vertical ballet video ending with the on-screen text "Elegance v pohybu", used as the title; uploaded by the owner, no brand or tool confirmed. Audio kept in the full file as for `wild-silk`.
10. `orange-hour` (Video and Fashion): 13 s vertical summer video in orange tones inspired by Alo, uploaded by the owner. Orange Hour is a working title; no tool confirmed. Audio kept.
11. `clover-gold` (Video and Product & Beauty): 14 s horizontal 16:9 jewellery video inspired by Dior clover earrings, uploaded by the owner. Clover Gold is a working title; no tool confirmed. Audio kept. The card preview crops the 16:9 clip to the card ratio; when played it switches to `object-fit:contain` (`.video-cover.is-landscape`).
12. `prague-pour` (Video and Product & Beauty): 10 s vertical video of an AI billboard on a Prague corner building, inspired by Kilian Paris Angels' Share; uploaded by the owner (file name suggests Higgsfield, not confirmed by the owner, so no tool is stated). Prague Pour is a working title. Disclosure states the billboard is AI-generated and not a real campaign. Audio kept.
13. `olive-tailoring` (Video and Fashion): 13 s vertical studio lookbook video, olive suit and gold earrings, uploaded by the owner. Olive Tailoring is a working title; no brand or tool confirmed. Audio kept.
14. `golden-departure` (Product and Fashion): menswear series with a leather messenger bag at a private jet at sunset, inspired by Polo Ralph Lauren, photos supplied by the owner. Golden Departure is a working title; no tool confirmed. Placed after the other photo projects, before the videos. 4 photos in supplied order: walk to the jet (cover), leather label detail, smiling portrait, lifting the bag at the airstairs.

Portfolio tabs (owner request): there is no "Vše/All" button. Three tabs — Product & Beauty (default), Fashion, Video — and each project belongs to exactly one tab so nothing repeats: product = lime-shot, sky-and-sand, honey-drip; fashion = clay-court-summer, soft-structure, daisy-meadow, golden-departure, parlour-hours; video = all video projects. The category descriptions in the list above describe content, not the tab. `showCategory()` sets `hidden` and `aria-pressed`; a `#slug` hash opens the right tab and scrolls to the card. `data-category` may still hold several space-separated values; the first one is used for hash navigation. Upload video as H.264 MP4 with `+faststart`.

## Pricing (Kč)

Individual services: associative photo 450; hero/model photo 750; video up to 15 s 1,850; up to 30 s 2,750; up to 60 s 3,900. Also individual only (not in packages): AI voiceover up to 10 s 450, up to 20 s 650 (synthetic AI voice, any language, no imitation of real people's voices), consultation 1,500 per hour — mentoring for beginner AI creators (where to start, which programs, workflow), not a brand consultation (`unitSuffixHour`); explained in two separate FAQs, `audioTitle`/`audioBody` and `consultTitle`/`consultBody` (the owner noted the two services are unrelated). Carousels were removed from the offer at the owner's request (no carousel unit price, package item or FAQ).

Monthly packages (names and contents chosen with the owner; she asked for more hero/model photos in each package):

| Package | Price | Contents | Individual total | Saving |
| --- | ---: | --- | ---: | ---: |
| ZÁBLESK | 6,950 | 8 associative photos + 3 hero/model photos + 1 video up to 15 s | 7,700 | 750 (9.7%) |
| RÁMEC | 8,600 | 12 associative photos + 6 hero/model photos | 9,900 | 1,300 (13.1%) |
| POHYB | 8,900 | 2 videos up to 15 s + 1 video up to 30 s + 1 video up to 60 s | 10,350 | 1,450 (14.0%) |
| PŘÍBĚH | 13,400 | 15 associative photos + 6 hero/model photos + 1 video up to 15 s + 1 video up to 30 s | 15,850 | 2,450 (15.5%) |
| VIZE | 22,900 | 25 associative photos + 9 hero/model photos + 2 videos up to 30 s + 1 video up to 60 s | 27,400 | 4,500 (16.4%) |

PŘÍBĚH is visually recommended. Preserve these prices and quantities unless the owner asks for changes. Existing terms: two rounds of minor revisions per deliverable; additional photo revisions 180 Kč/item, video 400 Kč/item; extras at individual rates; final scope, price and timing confirmed after consultation. Package item keys follow `package{n}item{k}` with k = 0 associative, 1 hero/model, 2 video 15 s, 3 video 30 s, 4 video 60 s.

## Content constraints

The owner wants AI disclosure and independent concepts presented accurately. Preserve current AI labels and AI & Transparency copy. Do not imply that the featured brands commissioned, sponsored or endorsed the concepts. Do not invent client names, client relationships, outcomes, testimonials, portfolio tools or creator achievements. Preserve supplied images and their proportions.

## Validation and publication

For edits, check JavaScript syntax, both language dictionaries including alt-text, local asset paths, anchor targets and changed behavior. For visual/layout work, check mobile and desktop in a browser when available. No browser visual QA was performed before this export.

This export has no original Git history, hosting configuration or credentials. It does not automatically update the existing hosted site. Keep changes local until the owner requests deployment through an available hosting workflow.

GitHub Pages: the repository `evasvision/evasvision.github.io` is published by GitHub Pages directly from the root of `main` (Deploy from a branch; `.nojekyll` disables Jekyll). The original export kept the site in `dist/`; it was moved to the root for Pages. EXPORT.json paths still use the `dist/` prefix. All asset paths are relative, so the site works from the domain root. The initial GitHub upload flattened files and lost the Clay Court Summer `portrait` and `overhead` images (name collision with Soft Structure); the owner re-supplied them at 1493×2000, so their checksums no longer match EXPORT.json.
