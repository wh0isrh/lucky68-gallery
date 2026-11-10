# Lucky68 — Language picker design

## Intent

First-time visitors should choose English or Simplified Chinese before entering the catalogue. Firebase Hosting's IP country match recommends Chinese for mainland China and English elsewhere; a returning visitor's saved manual choice takes precedence.

## Goals and constraints

- Keep the choice to one screen and one click, with both languages immediately recognizable.
- Remember a visitor's choice and skip the picker on later visits.
- Use Firebase Hosting's built-in country matching; do not send visitor IPs to another service.
- Keep static delivery compatible with Firebase Hosting and GitHub Pages, without new dependencies.

## Approaches

- **Full-screen language chooser (selected):** a restrained bilingual page with two large language choices; the detected default is marked as suggested. Directly addresses the request to choose at the beginning.
- Centered modal over the catalogue: keeps the catalogue visible but obscures the experience and feels less like an intentional language choice.
- Compact banner: least disruptive but easy to miss and too subtle for a first-visit choice.

## Interaction

At `/`, Firebase serves a country-specific entry file for mainland China and the default entry file elsewhere. Both open a shared language picker with the matching recommendation. Selecting English or Chinese saves that choice and opens the existing catalogue. Returning visitors with a saved choice go straight to the catalogue. Direct catalogue links continue to use the query language or English fallback.

## Visual direction

Use Lucky68's existing warm chalk, navy, quiet dividers, and restrained typography. Keep the screen sparse: wordmark, concise bilingual prompt, two equal choice cards, and a subtle location-based suggestion on the recommended option. No hero imagery or tutorial copy; the purpose is a quick choice.

## Non-goals

- Detecting location on GitHub Pages, which has no Firebase country matching.
- Inferring a visitor's preferred language from browser settings or collecting analytics.
