# obsidicore.com

Source for [obsidicore.com](https://obsidicore.com) — the one-page site for Obsidicore LLC.

Static site, no build step. One page of hand-written HTML and CSS in `public/`, zero JavaScript, deployed to Firebase Hosting.

## Layout

```
public/
  index.html          the one-pager
  404.html            not-found page
  favicon.svg         primary icon (obsidian shard with an ember glint)
  favicon.ico         32px fallback
  apple-touch-icon.png 180px icon for iOS
  og.png              1200x630 social card
  site.webmanifest    PWA manifest
  robots.txt
  sitemap.xml
firebase.json         hosting config (site: obsidicore-web) + security headers
.firebaserc           Firebase project alias (lavalab-dev)
```

## Deploy

Prerequisite: `firebase login`, and the Hosting site created once:

```
firebase hosting:sites:create obsidicore-web --project lavalab-dev
```

Then deploy:

```
firebase deploy --only hosting --project lavalab-dev
```

This serves at `https://obsidicore-web.web.app`. To put it on the apex domain, add
`obsidicore.com` under Firebase console → Hosting → Add custom domain, then enter the
TXT + A records it issues at the DNS host.

## Notes

- The `public/index.html` copy is final and matches `design/copy-deck.md` in the handoff kit.
- The photo slot in the "Who" section is a placeholder (`GL`) until Geoff supplies a headshot.
- Security headers (strict `Content-Security-Policy` with no script sources, HSTS, `nosniff`, frame denial) live in `firebase.json`.

Code is MIT (`LICENSE`). Site copy © Obsidicore LLC.
