The repository is a small static landing site for CoinCarriere (two main pages: `home.html` and `landing-page-recruiter.html`). These instructions give concise, actionable guidance for AI code agents working here.

1) Big picture
- Purpose: marketing/landing pages for a recruitment platform (candidate + recruiter funnels). Files are plain HTML with inline Tailwind + small JS (no server-side code in repo).
- Primary artifacts: `home.html` (candidate-facing home page) and `landing-page-recruiter.html` (B2B recruiter landing). Both are standalone HTML documents that include Tailwind via CDN and inline scripts/styles.

2) What you can safely modify
- Content updates: headings, copy, links, static counts and badges shown in the pages (e.g. "4943+ offres" in `home.html`).
- Layout and styling: adjust Tailwind classes or inline CSS blocks. The project uses CDN Tailwind; do not add a local Tailwind build unless requested.
- Small client-side behavior: the inline countdown script in `home.html` and simple DOM interactions used for cookie consent. Keep changes minimal and test by opening the file in a browser.

3) What to avoid or flag
- Do not add server or backend code — repo contains only static pages. If a feature requires APIs, describe the API contract in PRs instead of adding network calls.
- Avoid adding heavy build tooling or large dependencies. The repository currently has a minimal `package.json` with only a devDependency (`opencode-ai`) — do not change deps without the maintainer's consent.

4) Project-specific patterns and notes
- CDN-first assets: Tailwind and Lucide icons are loaded from CDNs. When suggesting changes, reference the CDN usage (e.g. update `https://cdn.tailwindcss.com` config block) instead of switching to a local build.
- Inline design tokens: colors and fonts are configured inside a `tailwind.config = { ... }` script tag. If you change color names used across the file, update all occurrences (examples: `primary`, `lime-btn`, `glass-card`, `navy`, `teal`).
- Small JS utilities: `home.html` contains a countdown timer (target date: 2026-06-15). If adjusting time-based UI, preserve `setInterval` usage and guard for invalid dates (as current code does).
- Images: many images point to `https://cdn.coincarriere.com/` or Unsplash. Prefer leaving CDN links unless the task specifically involves replacing images.

5) Editing and commit guidance for agents
- Keep diffs small and focused (one UI change per PR). Provide a short description at top of the file when you modify copy or UX (e.g. "ui: update hero copy + CTA style").
- When changing text (copy/translation), update both pages if the same phrase appears in both files (search for the string). Use the existing French language of the site.

6) Examples of actionable changes
- Update hero numbers: edit the text node in `home.html` near the top: "Trouvez votre prochain emploi parmi 4943+ offres actives" and update any matching counters elsewhere.
- Change primary color shades: edit the `tailwind.config` block inside `home.html` and `landing-page-recruiter.html` where extensions to `colors` are defined; keep the same keys (`primary`, `navy`, `teal`, `lime`) to avoid breaking class names used in markup.
- Improve accessibility: add alt text where images are missing descriptive text; example — search for `<img src="logo.jpeg"` in `landing-page-recruiter.html` and replace with a full CDN URL or meaningful alt copy.

7) Local testing instructions (quick)
- These are static HTML files — open them in a browser to inspect changes. From project root you can run a simple static server if you prefer live reload. Example commands (optional):

```bash
# serve via Python 3 built-in server
python3 -m http.server 8000
# then open http://localhost:8000/home.html
```

8) Useful file references
- `home.html` — candidate landing page, main hero + countdown + features.
- `landing-page-recruiter.html` — recruiter-focused landing with process steps and CTAs.
- `package.json` — minimal; do not change dependencies lightly.

9) If you need to add tests or tooling
- Note: repo currently has no test framework. Propose tests or CI changes as a separate PR and document the reason. Keep first PRs to content/styling/HTML only.

10) When to ask the maintainer
- Any change that introduces build tooling, new dependencies, or server-side components.
- Replacing CDN-hosted assets with local builds.

If anything in these instructions is unclear or you'd like more detail (e.g., canonical image CDN path, or target browsers), tell me which area to expand and I will iterate.
