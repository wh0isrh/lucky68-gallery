# Lucky68 catalogue redesign

**Status: approved and implemented.**

## Intent

Refresh the Lucky68 public catalogue for visitors who browse fashion products, inspect album photos, and follow existing product links. The visual direction combines a little of Yupoo’s direct, brand-first catalog browsing with Apple-like restraint and editorial image quality. It must feel intentionally art-directed, not generically generated.

## Goals

- Make the clothing images and brand sections lead the experience.
- Keep the 120 albums, 1,169 photos, external product/photo links, English/Chinese switch, brand filter, search, sorting, and expandable photo grids working.
- Improve browsing density and brand navigation while keeping each image fully legible and uncropped.
- Adapt relevant patterns from `website-cloner`: `RevealText` for restrained word-by-word introductory motion, `Action` for a small reusable link-control treatment, and the image-led `Creator` cards for album media behavior.
- Keep the site as a static, dependency-free HTML page on GitHub Pages.

## Non-goals

- No checkout, cart, accounts, backend, new product data, or changed source links.
- No wholesale migration to Next.js and no edits to `website-cloner`.
- No colorful Javii lettering, floating widgets, or heavy animation.

## Approaches considered

1. **Adapt selected components in the current static page (chosen).** Port the useful markup and interaction patterns from the cloner into Lucky68’s existing HTML/CSS/JS. Preserves deployment and data behavior; requires a careful static adaptation because the original components depend on React.
2. **Migrate Lucky68 to Next.js and import React components.** Gives literal component reuse, but changes the build/deployment model and introduces unnecessary framework/runtime work for this static archive.
3. **Restyle Lucky68 without using cloner components.** Lowest technical effort, but ignores the request to reuse the referenced work.

## Proposed direction

A **brand-led fashion showroom index**: compact Yupoo-like brand wayfinding and dense album browsing sit inside a warm, quiet editorial shell. Use a pale stone ground, black/graphite typography, fine silver rules, generous image areas, and the existing brand marks as the only strong color. Use one display serif for the lead line and a precise sans for controls and metadata. Product photographs stay prominent and use `object-fit: contain`.

### First viewport

A slim Lucky68 masthead with the EN / 中文 switch; a compact editorial title and album/photo totals; a visible brand index; then the sticky search/filter/sort row and the first image-led album cards. Keep the first actual product image visible near the fold rather than spending the opening screen on an oversized decorative hero.

### Visitor path and interaction

Visitors can jump to a brand, search titles/photo names, filter or sort, open an album to inspect its full photo grid, and follow the existing product or ImgBB links. Use the cloner’s `RevealText` timing on the short intro and its image-card hover discipline on album covers; keep album expansion as the meaningful interaction. Motion is subtle, content remains visible when reduced motion is requested, and keyboard focus remains clear.

### Responsive behavior

Desktop gets a compact brand index and image-rich multi-column catalogue. On narrow screens, the brand index becomes horizontally scrollable, controls wrap cleanly, and album cards use a balanced two-column layout where space allows. Photo grids remain uncropped and never overflow horizontally.

## Constraints and risks

- Images remain hosted by ImgBB, so image availability and loading depend on ImgBB and the visitor’s network.
- GitHub Pages must continue to serve the page without a server or build pipeline.
- The cloner’s components are React and cannot be imported into standalone HTML; their selected patterns will be adapted, not copied as runtime imports.
- No new dependencies. Existing content and outbound links remain authoritative.

## Implementation and review plan

1. Replace the current visual skin in the canonical `index.html` while preserving its embedded data and behavior.
2. Adapt only the selected component patterns and keep existing local brand SVGs.
3. Sync the user-facing gallery deliverable and update repository documentation as needed.
4. Inspect desktop and mobile renders, verify English/Chinese and album/photo interactions, run the Impeccable detector, then commit and publish from the command line.

## Outcome

Approved direction delivered in the existing dependency-free HTML page. The oversized hero title was removed after visual review; the compact intro, album/photo totals, brand index, controls, and first product cards now lead the page. Desktop and mobile layouts, English/Chinese switching, brand jumping, live search, and expanded photo display were visually inspected. The Impeccable detector reported one slightly low placeholder contrast; the muted token was darkened to address it.