# Craft checklist pass — 2026-08-03

## Product type

Long content / narrative docs page (Bitcoin whitepaper CN translation). Vanilla HTML + CDN markdown/MathJax. Perfect fit for **附 A Premium One-pager**.

## Already present

- Custom OG / Twitter cards + `assets/og-image.png`
- JSON-LD Article / WebPage / Breadcrumb
- `scroll-behavior: smooth`
- Loading state + error state with CTA links (Raw / GitHub)
- Security-ish `_headers` (nosniff, referrer, permissions)
- Paper/amber brand tokens (`#c86a22`, `#faf6ee`)

## Implemented this pass

附 A full pack (brand-tuned amber/paper, not default sage):

| Item | Files |
|---|---|
| Top 3px scroll progress | `assets/premium-one-pager.css`, `assets/premium-one-pager.js`, wired in `index.html` |
| One-shot viewport reveal (`h2` / img / blockquote / table; **not** hero `h1`) | same + `prepareCraftTargets()` in `index.html` |
| Chapter dots 01–12 from numbered `h2[data-chapter]` | same; `sectionSelector: "[data-chapter]"`, `maxChapters: 12` |
| SVG feTurbulence noise overlay | same |
| Thin scrollbar + `::selection` + smooth scroll + `prefers-reduced-motion` kill-switch | same |

Non-visual cheap wins:

| Item | Files |
|---|---|
| Honest loading stages (deps → read zh.md → render → typeset) | `index.html` |
| Error copy includes concrete failure detail + next actions | `index.html` |
| Skip link + `:focus-visible` on chrome/content links | `index.html` |
| Deep-linkable heading ids + hash restore after render | `index.html` |
| Cache headers for new craft assets | `_headers` |

## Explicitly skipped

- Skeleton screen — content is one markdown fetch; staged copy is enough
- Cmd+K / undo / autosave — not an app shell
- Dynamic OG per section — static article OG already shipped
- Changelog page / status page — out of scope for this content archive
- Rewrite of translation copy

## Residual P2/P3

- P2: Offline / service-worker for zh.md when GitHub raw fallback is slow
- P2: Footnotes back-link focus ring polish under github-markdown-css
- P3: Print stylesheet (progress/noise/dots hidden)
- P3: Optional toc drawer on mobile (desktop dots hidden ≤900px)

## Verification

- Static checks: CSS/JS linked, one-shot `unobserve`, brand tokens, no `pop-reveal` on `h1`
- `node --check` on `assets/premium-one-pager.js`
- Local `python3 -m http.server`: `index.html` / craft CSS / JS / `zh.md` → 200
- Not verified in a real browser session this pass (no commit/push/deploy)
