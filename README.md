# No Code Society website

A website concept for UNSW No Code Society, the builders collective that teaches students to ship real products with no-code and AI tools.

The whole site is one 3D world drawn in the same black-and-white stipple as the NCS logo. Scrolling plays it like a film: the camera moves through the world while each chapter's text cuts in place.

- **Home:** the logo, alive. The planet's lit edges follow your cursor; click the planet for a shockwave.
- **Purpose:** what NCS is for, how it works, real event photos (hover for colour) and the five portfolios as moons.
- **Education:** voxels spell each tool taught (Notion, A1Zap, Framer, Base44, Sym AI) as you scroll the workshops.
- **Projects:** member builds assemble on a pedestal (CampusSync, Quad, LifeMaxxing, Your build), then the hackathon log.
- **Team:** the 2027 exec as orbiting satellites.
- **Join:** links to Instagram, LinkedIn and Linktree.

Sound is off by default; turn it on bottom left.

## Run it

It is a static page with no build step. Open `index.html` through any local server, for example:

```bash
python3 -m http.server 8000
```

then visit http://localhost:8000.

## Edit it

All text is plain HTML inside the `.stage` blocks in `index.html`. See `HANDOVER-PROMPT.md` for how the chapters, beats and 3D pieces connect, and for a prompt that lets a coding agent swap this in for an existing site or merge it with one.

Built by Hugh Phan (Projects).
