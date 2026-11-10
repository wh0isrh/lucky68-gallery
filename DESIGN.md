# Lucky68 Gallery — Design Notes

## Product

A public bilingual catalogue for visitors who browse product albums and open the original product or photo links. The collection contains 120 albums and 1,169 photos. Product data and source URLs remain authoritative.

## Visual system

- Warm chalk canvas with restrained ink, graphite labels, cool gray dividers, and navy interaction states.
- Compact Lucky68 masthead, English / 中文 toggle, short intro, collection totals, and horizontally scrollable brand index.
- Sticky search, brand filter, and sort controls directly above the catalogue.
- Brand sections use locally stored logos and bilingual names with album and photo counts. Titles containing `T N F` are grouped under The North Face.
- Album covers and expanded photo thumbnails use `object-fit: contain` so garments remain fully visible.
- Four-column desktop browsing adapts to two columns on mobile. Reduced-motion preferences disable transitions and smooth scrolling.

## Interaction

Visitors can search album titles and photo names, filter by brand, sort the collection, jump to a brand, expand each album's photos, and open existing external links. The language switch updates interface copy while retaining source titles.

## Implementation

Single-file HTML/CSS/JS with embedded catalogue data and local SVG brand marks. No dependencies or build step. Useful `RevealText`, `Action`, and image-card interaction patterns from `C:\Users\alex\Documents\Projects\website-cloner` were adapted for static delivery.

## Review

Visually inspected at desktop and 390px mobile widths. Confirmed the English toggle, Moncler search results (30 albums), brand jump, and expanded photo thumbnails. The Impeccable detector found a placeholder contrast of 4.4:1 against a 4.5:1 target; the muted token was darkened from `#777a74` to `#6d706b`.