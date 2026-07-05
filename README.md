# Reagan Brooks LLC — reaganbrooks.com

A single, static holding page. No CMS, no build step, no JavaScript, no
tracking. It renders fully with JavaScript disabled.

## Files

```
index.html            The page (one scroll, three quiet sections)
styles.css            All styling; palette fixed to five tokens
robots.txt            Allows indexing
sitemap.xml           One URL
assets/
  wordmark-navy.svg   Stacked REAGAN / rule / BROOKS — Slate Navy
  wordmark-bone.svg   Same, Bone (for use on Slate Navy)
  monogram-navy.svg   Ruled-square R / rule / B — Slate Navy (favicon/touch icon)
  monogram-bone.svg   Same, Bone (used in the contact section)
  fonts/
    eb-garamond-latin-roman.woff2    weights 400–500
    eb-garamond-latin-italic.woff2   weights 400–500
```

## Deploy

It is plain static files. Point any static host at the repository root:

- **Netlify / Cloudflare Pages:** no build command, publish directory `/`.
- **S3 / any bucket:** upload the tree as-is; set `index.html` as the index document.

No environment variables, no server code.

## Brand constants (do not deviate)

Palette — these five values only. No pure white, no pure black.

| Token | Hex | Role |
|---|---|---|
| Slate Navy | `#1C2C3E` | Headlines, marks, rules |
| Antique Brass | `#8B6F3F` | Single accent |
| Bone | `#F5F1E8` | Page background |
| Stone Gray | `#6B6358` | Secondary text, fine print |
| Ink | `#2D2A26` | Body copy |

Type is **EB Garamond only**. The marks are used as SVG files and are never
redrawn as live text.

## Notes for the client

Two bracketed placeholders are left in `index.html` for you to fill before
launch:

- **Email** — `[general@reaganbrooks.com]` in the contact line. Confirm the
  address and remove the brackets (update both the visible text and the
  `mailto:` link).
- **Year** — `[Year]` in the footer copyright.

## Decisions worth flagging

- **Fonts are self-hosted, not loaded from Google Fonts.** The brief asked for
  EB Garamond via Google Fonts, but also required *no third-party embeds and no
  tracking*. Serving the font from Google's CDN is a third-party request. The
  two reconcile by self-hosting the same font (latin subset, `woff2`), which
  keeps the page free of any outbound third-party call while still using
  EB Garamond exactly. The roman face is preloaded so no fallback flashes.
- **The four marks were drafted for this build** from EB Garamond letterforms
  as true vector outlines (no font dependency at render time). They are a
  first-draft interpretation of the wordmark and monogram — review and replace
  with final artwork if the firm has official files.
- **No JavaScript at all** — guarantees the page renders with JS disabled and
  produces zero console errors.
