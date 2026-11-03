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

Seventeen gallery projects exist:

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

15. `frame-of-mind` (Product & Beauty): eyewear editorial with tortoiseshell cat-eye glasses, inspired by Miu Miu, photos supplied by the owner. Frame of Mind is a working title; no tool confirmed. Placed after `honey-drip`. 5 photos (1493×2000): cover is the owner-chosen reaching-hand shot, then close-up lowering the glasses, glasses held to camera, peering through blinds, seated on a chrome chair.

16. `late-night-call` (Video): 15 s vertical horror-parody short film promoting Eva’s Vision itself — a girl on the phone on a pink bed while a white-masked figure at the window opens it and steals a pink evas_vision box. Uploaded by the owner (file name suggests Higgsfield, not confirmed, so no tool stated). Late Night Call is a working title; no external brand. Re-encoded from HEVC to H.264 (24 fps), audio kept; poster is the frame at 2 s. Placed last, after `olive-tailoring`.

Portfolio tabs (owner request): there is no "Vše/All" button. Three tabs — Product & Beauty (default), Fashion, Video — and each project belongs to exactly one tab so nothing repeats: product = lime-shot, sky-and-sand, honey-drip, frame-of-mind; fashion = clay-court-summer, soft-structure, daisy-meadow, golden-departure, parlour-hours; video = all video projects. The category descriptions in the list above describe content, not the tab. `showCategory()` sets `hidden` and `aria-pressed`; a `#slug` hash opens the right tab and scrolls to the card. `data-category` may still hold several space-separated values; the first one is used for hash navigation. Upload video as H.264 MP4 with `+faststart`.

## Pricing (Kč)

Updated 2026-11-03 at the owner's request. The authoritative pricing copy is the last `Object.assign(copy.cs/en, …)` block before `setLanguage` (it overrides older pricing keys still present in earlier blocks) plus the static `#pricing` HTML.

Individual services: associative photo 550; hero/model photo 950; video up to 10 s 1,690; up to 15 s 2,290; up to 30 s 3,590; up to 60 s 5,490; AI voiceover up to 10 s 490, up to 20 s 790; consultation 1,800 per hour (mentoring for beginner AI creators); extra revision photo 250, video 600. Unit rows use keys `uPhotoA`, `uPhotoH` (+ `…Hint`), `uV10`–`uV60`, `uVo10`, `uVo20`, `uRevPhoto`, `uRevVideo`, `unit7`.

PILOT (one-off, first collaboration only): 3 associative + 2 hero/model + 1 video up to 10 s = 3,790 (individually 5,240, save 1,450, 28%). Shown as `.pilot-card` above the packages.

Monthly packages (every package mixes photos and video; RÁMEC = photo focus, POHYB = video focus, same price):

| Package | Price | Contents | Individual total | Saving |
| --- | ---: | --- | ---: | ---: |
| ZÁBLESK | 7,290 | 8 associative + 2 hero/model + 1 video 15 s | 8,590 | 1,300 (15%) |
| RÁMEC | 11,190 | 12 associative + 5 hero/model + 1 video 15 s | 13,640 | 2,450 (18%) |
| POHYB | 11,190 | 6 associative + 2 hero/model + 2 videos 15 s + 1 video 30 s + 1 voiceover 10 s | 13,860 | 2,670 (19%) |
| PŘÍBĚH | 15,690 | 14 associative + 5 hero/model + 2 videos 15 s + 1 video 30 s | 20,620 | 4,930 (24%) |
| VIZE | 24,690 | 22 associative + 8 hero/model + 2 videos 15 s + 1 video 30 s + 1 video 60 s + 1 voiceover 10 s | 33,850 | 9,160 (27%) |

Package bonuses (`.package-bonus`): PŘÍBĚH and VIZE get 3 revision rounds instead of 2 and 10% off extra content; VIZE also a short concept call at the start of the month and priority scheduling. PŘÍBĚH is visually recommended. Package item keys `package{n}item{k}`: k = 0 associative, 1 hero/model, 2 video 15 s, 3 video 30 s, 4 video 60 s, 5 voiceover 10 s.

Referral (owner request): whoever recommends Eva gets 10% off their next order when the referred client starts working with her (`.referral` block + `refFaqTitle`/`refFaqBody`). Delivery up to 2 working days; 2 rounds of minor revisions per deliverable; final scope, price and timing confirmed after consultation. Preserve these prices and quantities unless the owner asks for changes.

## About copy

Owner-supplied facts for the About section: Eva is 25, an AI creator in Prague and a curator of the Czech AI course "AI New Era"; she values realism and avoiding generic "AI slop". The copy is a hook-led lead (`aboutLead`), two body paragraphs, a punch line and three fact chips. Do not add other achievements.

Privacy note (`l4`/`l4d` in AI & Transparency) was rewritten in plain language for GitHub Pages hosting: no trackers, only the language choice stored locally, GitHub Pages may log technical data such as IP, e-mail/Instagram details used only to reply.

## Content constraints

The owner wants AI disclosure and independent concepts presented accurately. Preserve current AI labels and AI & Transparency copy. Do not imply that the featured brands commissioned, sponsored or endorsed the concepts. Do not invent client names, client relationships, outcomes, testimonials, portfolio tools or creator achievements. Preserve supplied images and their proportions.

## Validation and publication

For edits, check JavaScript syntax, both language dictionaries including alt-text, local asset paths, anchor targets and changed behavior. For visual/layout work, check mobile and desktop in a browser when available. No browser visual QA was performed before this export.

This export has no original Git history, hosting configuration or credentials. It does not automatically update the existing hosted site. Keep changes local until the owner requests deployment through an available hosting workflow.

Custom domain: evasvision.cz (registered at Active24, DNS at Active24: four A records 185.199.108–111.153 for the apex, CNAME www → evasvision.github.io; mail records MX/TXT/mail.* untouched; the Active24 Web auto-config must stay off). The `CNAME` file is managed by GitHub Pages settings — do not delete it. Enforce HTTPS is set in Settings → Pages once the certificate is issued. evasvision.github.io redirects to the domain.

GitHub Pages: the repository `evasvision/evasvision.github.io` is published by GitHub Pages directly from the root of `main` (Deploy from a branch; `.nojekyll` disables Jekyll). The original export kept the site in `dist/`; it was moved to the root for Pages. EXPORT.json paths still use the `dist/` prefix. All asset paths are relative, so the site works from the domain root. The initial GitHub upload flattened files and lost the Clay Court Summer `portrait` and `overhead` images (name collision with Soft Structure); the owner re-supplied them at 1493×2000, so their checksums no longer match EXPORT.json.
