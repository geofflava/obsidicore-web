# AGENTS.md — obsidicore-web

Company one-pager for Obsidicore LLC (obsidicore.com). Hand-written static HTML/CSS on
Firebase Hosting. No framework, no build step, no JavaScript — a product decision, not
an omission.

Pages: `public/index.html`, `public/404.html`. Each page carries its own inline
`<style>`; a shared rule must be added to both pages when it applies to both.

## Hard rules

- Zero JavaScript. CSP is `default-src 'none'` with inline styles. Never add `<script>`,
  external fonts, CDN links, images from other hosts, or new CSP directives.
- Design tokens in `:root` are locked (obsidian / glass / ink / ash / ember / go). Button
  ink is `#1a0d05`.
- This is the cool, calm sibling of lavaforge.dev: obsidian and glass, not basalt and
  ember. The split is deliberate ("obsidian is what lava becomes when it cools fast") —
  do not import lavaforge's warm furniture, ember glows, cursors, or logbook decorations.
  When in doubt, quieter.
- Copy is pre-approved and arrives verbatim in the work package. Do not write, rewrite,
  or "improve" prose, titles, or metadata. Banned everywhere: bare "agent readiness",
  "AOSF", "Senior", "built in public" as a written claim. Headings are sentence case.
- Motion is opt-in. Every `transform`/`animation` lives inside
  `@media (prefers-reduced-motion: no-preference)` or has a `reduce` fallback landing on
  the fully visible end state. Never `opacity: 0` in base styles. Compositor properties
  only (`transform`, `opacity`); name transitioned properties, never `all`. Scroll-driven
  rules additionally sit inside `@supports (animation-timeline: view())`.
- Lighthouse (mobile) stays 100/100/100/100. Contrast stays AA. CLS stays 0.

## Verify loop (run before reporting, every task)

1. Serve `public/` (e.g. `python -m http.server 8080`) and check both pages at 1440px and
   375px viewports.
2. Hover and focus every link, button, and row you touched; Tab through from the top.
3. Re-run with reduced motion emulated: no transforms fire, nothing hidden.
4. Console: zero errors. Network panel: zero external requests.

## Git

- Commit locally with clear messages. Never push, never deploy, never touch remotes or
  `firebase.json` — a human gates both.
- Don't touch `favicon.*`, `og.png`, `robots.txt`, `sitemap.xml`, or `assets-src/` unless
  the package says so.
- If the package conflicts with what you find in the files, stop and report the conflict
  instead of improvising.
