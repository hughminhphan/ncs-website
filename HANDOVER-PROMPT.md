# Handover prompt

Paste everything below the line into Claude Code, Cursor, Codex or any coding agent, run from inside the repo that hosts the current No Code Society website (or an empty folder if there is no site yet).

---

You are helping UNSW No Code Society (NCS) adopt a new website design. The new site lives at https://github.com/hughminhphan/ncs-website. It is a single static page: `index.html` plus three photos in `img/`. It has no build step and no framework. It loads three.js 0.160.0 and Lenis 1.1.13 from public CDNs and two Google Fonts (Silkscreen, Geist Mono).

How the new site works, so you do not break it:
- A fixed full-screen WebGL canvas renders one 3D world (a planet, orbits, voxel words, a pedestal, satellites) through a 1-bit ordered-dither post pass. That black-and-white stipple look is the NCS logo's look and is the brand. Keep it.
- `<main>` holds empty spacer sections, one per chapter (`#home`, `#purpose`, `#education`, `#projects`, `#team`, `#join`). Each spacer's height is its number of beats times one screen (`data-beats` and `style="height:Nsvh"` must agree).
- Each chapter's visible content is a `.stage[data-ch="…"]` with one `.beat` per screen. Only the active stage and beat show; the camera path is the `K` (desktop) and `NARROW` (phone) objects in the script.
- Education beats map to the voxel words in `WORDS` (in order). Projects beats map to the 3D artifacts in `arts` (in order). Team rows (`#crew .row`) map to the satellites in order.
- Text rules: headings scramble in, other text cuts on. No fades, no blur-ins, no text rising through a mask.

Step 1: Work out which situation you are in, then tell me before changing anything.
- A. There is no existing site, or the existing site should be fully replaced ("switchover").
- B. There is an existing site with content or features we must keep ("combine").
To decide, list what the current site has: pages, routes, blog posts, event listings, sign-up or membership forms, sponsor pages, analytics, SEO metadata, custom domain and DNS setup, redirects, and anything that reads from a CMS or database. Show me that inventory and your recommendation, A or B.

Step 2A: Switchover.
1. Copy `index.html` and `img/` from the new repo into the hosting repo (or deploy the new repo directly: GitHub Pages, Vercel, Netlify and Cloudflare Pages all serve it as is).
2. Keep the existing domain, favicon, analytics snippet and any verification meta tags; move them into the new `<head>`.
3. Add 301 redirects from every old URL to the closest new anchor (for example `/about` to `/#purpose`, `/events` to `/#education`, `/team` to `/#team`) so old links and search results still work.
4. Update the facts before launch: check the exec list, workshop dates, hackathon results and stats against current NCS records, and replace anything out of date. Every fact on the page is in plain HTML inside the `.stage` blocks.

Step 2B: Combine.
1. Keep the new design as the home page. Do not try to restyle the old pages into the WebGL layout.
2. Move any existing content worth keeping into the new structure where it fits:
   - Mission or about text goes into the Purpose beats.
   - Workshops and events go into Education beats (one beat per workshop; add the tool name to `WORDS` using only letters the 5x7 `FONT` defines, or add glyphs to `FONT`).
   - Projects go into Projects beats (one per project; each needs a matching artifact in `arts`, or reuse the "Your build" artifact).
   - People go into the Team crew list.
   When you add or remove a beat, update that chapter's `data-beats` and spacer height to match.
3. Content that does not fit a pinned one-screen beat (long blog posts, full event archives, forms, sponsor packs) stays as separate plain pages. Restyle them with the same tokens (`--paper #e9e9e4`, black background, `--signal #ffde4a` for the one call to action, Silkscreen for headings, Geist Mono for everything else) and link to them from the Join chapter and the top nav.
4. Keep every existing URL working through redirects or by leaving those pages in place.

Step 3: Check before shipping.
- Open the page on a desktop browser and a phone. Scroll the whole way through; every chapter's text must sit clear of the top nav and bottom HUD, and nothing may scroll sideways on a phone.
- Click each nav tab; it must land on that chapter.
- Turn sound on (bottom left) and confirm it plays only after the click.
- Check the browser console for errors and confirm the three photos load.
- Report what you changed, what you kept from the old site, and any URLs you redirected.
