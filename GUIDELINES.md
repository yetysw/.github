# yety guidelines

How a yety project looks, reads and is built. Written so that anyone, person or program, can start a new project that sits next to the existing ones without asking. Free to read and reuse.

Reference implementations, all public: [mccb](https://github.com/yetysw/mccb), [Jade](https://github.com/yetysw/jade) and [mccs](https://github.com/yetysw/mccs). yety builds tools that make sysadmins' lives better, among other things. These rules come from the [selfhostr guidelines](https://github.com/selfhostr/.github/blob/main/GUIDELINES.md); DumbMonit and SuckerPot, cited below as examples, are yety projects. Existing yety tools move to these rules when they are next worked on.

Words: **must** is a rule, **should** is the default, **may** is free. Where existing projects differ, the section says so and gives the rule for new ones.

---

## 1. Principles and voice

- **Honest about limits.** Every project has a "Limits" or "What it does not do" section, on the site and in the README. Keep every warning at full strength. Never oversell, never write "military grade", "blazing", "revolutionary".
- **Simple.** Few moving parts, sane defaults, one way to do a thing. If a feature needs a paragraph of caveats, cut it or document the caveat first.
- **Open source, MIT, free for good.** Licence is MIT. No paid edition, no feature held back, no open-core. Say so: "MIT, no paid edition". Dependencies must be under OSI-approved licences, enforced in CI.
- **Docker first.** The main install path is `docker compose up -d` from a published image. Show it as three commands or fewer.
- **Audience: sysadmins.** People who run a homelab, a server room or a team's infrastructure. Write for them: exact commands, ports, paths, what is stored where, how to back up, how to upgrade. No marketing fog.
- **Never call a project "small", "tiny" or "lightweight" as a selling point.** Describe what it does. (Naming a real limit of the audience, such as "teams who trust each other", is fine.)
- **Authors by handle only.** People appear as their GitHub handle (`@laupernoe`, `@Theroxat`), never a real name, photo or email. No member cards.
- **Voice.** Plain, short, concrete. Active voice. Explain it as you would to a friend who runs a home server. English is the source language of every text. No em dash anywhere (comma, colon or a new sentence). No emoji in prose or UI copy. Numbers stay exact.
- **No third parties on the site.** No analytics, no trackers, no external fonts, no CDN scripts. Everything is served from the site itself.
- **Claims must be checkable.** Anything the site says (version, supported devices, features) comes from the repository, the latest release or the docs. Do not state what you cannot point to.

## 2. Naming

| Thing | Rule | Example |
|---|---|---|
| Project name in prose | As written in the README title. Lowercase for newer projects | `mccb`, `jade` |
| New project name | **Lowercase, one word, no hyphen, no version** | `mccb` |
| Repository | `github.com/yetysw/<name>`, lowercase | `yetysw/mccb` |
| Site | `<name>.open.yety.ch` | `https://mccb.yety.ch` |
| Docs | `https://<name>.open.yety.ch/docs/` | |
| Demo | `https://<name>.open.yety.ch/demo/` | |
| Images | `ghcr.io/yetysw/<name>`, plus `-agent` or another suffix for a second image | `ghcr.io/yetysw/dumbmonit` |
| Image tags | `X.Y.Z`, `X.Y`, `latest` (stable), `edge` (from `dev`) | |
| Cloudflare Pages project | Same as the subdomain | `mccb` |
| Env variables | `<NAME>_*` upper case | `DUMBMONIT_VM_URL` |
| Metrics | `<name>_*` snake case | `dumbmonit_*` |
| Tokens | Short prefix of the name | |
| Versions | `0.MINOR.PATCH` until 1.0. Fix only: patch. New feature: minor. Tags `vX.Y.Z` | `v0.14.0` |
| Branches | `feat/…`, `fix/…`, `docs/…`, `chore/…` | `docs/guidelines` |
| Commits and PR titles | Conventional Commits | `feat(snmp): add MikroTik profile` |

Names are written the same in every language and never translated. Never use another company's name, mark or style in a name or logo. If a project talks to a third-party service, say "Not affiliated with X" in the footer.

Renaming a project keeps the old env variables, paths and tokens as read-only fallbacks for at least one minor version, and the README says so in one line.

## 3. Visual identity

Sites are **dark only**. Apps follow section 6.

### 3.1 Tokens

Copy these exactly. A project changes only the three `--accent*` values.

```css
:root{
color-scheme:dark;
--c-canvas:#07080a;--c-canvas-deep:#050607;--c-surface:#0b0d10;--c-surface-2:#111419;
--c-line:#16191e;--c-line-strong:#23272e;
--c-ink:#eceef1;--c-ink-2:#8a919c;--c-ink-3:#7a818c;--c-ghost:rgb(236 238 241 / .08);
--c-signal:#2fd17c;--c-signal-ink:#7be3a8;--c-signal-soft:rgb(47 209 124 / .12);
--c-advisory:#f2b033;--c-advisory-ink:#f7c766;--c-advisory-soft:rgb(242 176 51 / .13);
--c-warning:#ff5c5c;--c-warning-ink:#ff8a8a;--c-warning-soft:rgb(255 92 92 / .13);
--c-info:#7da9ff;--c-info-ink:#b3ccff;--c-info-soft:rgb(125 169 255 / .13);
--c-primary:#004AAD;--c-on-primary:#ffffff;
--shadow-lift:0 1px 0 rgb(255 255 255 / .02) inset,0 1px 2px rgb(0 0 0 / .5);
--shadow-float:0 2px 8px rgb(0 0 0 / .5),0 24px 48px -16px rgb(0 0 0 / .8);
--font-ui:'Inter','Segoe UI',system-ui,sans-serif;
--font-code:'JetBrains Mono',ui-monospace,monospace;
--radius-plate:6px;--radius-btn:8px;--radius-card:12px;--gutter:16px;
--ease:cubic-bezier(.16,1,.3,1);
--accent:#004AAD;--accent-ink:#7AA7F0;--accent-rgb:0 74 173;
}
@media (min-width:600px){:root{--gutter:24px}}
```

`<meta name="theme-color" content="#07080a">` and `<meta name="color-scheme" content="dark">` on every page.

### 3.2 Brand colour

Every yety site, doc and app uses one colour: **`#004AAD`**. There is no per-project colour.

| Token | Value | Use |
|---|---|---|
| `--accent` | `#004AAD` | Logo ground, buttons and filled surfaces, with white text (8.1:1) |
| `--accent-ink` | `#7AA7F0` | Links, icons, the rotating hero word and focus on dark grounds (8.2:1 on `#07080a`) |
| `--accent-rgb` | `0 74 173` | Tints and borders |

`#004AAD` on a dark ground reaches only 2.5:1: never use it for text there. On a light ground it is the text colour too (7.6:1). Never use it for status. Status colours (`signal`, `advisory`, `warning`, `info`) keep their meaning everywhere.

### 3.3 Logo

- SVG, `viewBox="0 0 64 64"`, a **rounded square** `<rect width="64" height="64" rx="15">` as ground, one simple glyph inside on the same grid, stroke widths 3 to 4.5, `stroke-linecap="round"`.
- Ground is `#004AAD` with a white glyph.
- Must read at 16 px, no text, no gradient, no more than three colours.
- Files at the root of the site: `favicon.svg`, `apple-touch-icon.png` (180), `og.png` (1200 x 630, the logo, the name, one sentence). Also keep PNG at 192, 512 and a maskable 512 for installable apps.
- The organization logo is a white Y on a `#004AAD` rounded square.

Example (mccb):

```html
<svg width="24" height="24" viewBox="0 0 64 64" aria-hidden="true"><rect width="64" height="64" rx="15" fill="#17181c"/><path d="M12 21c11 0 13 11 24 11M12 43c11 0 13-11 24-11M36 32h10" fill="none" stroke="#ecedef" stroke-width="4.5" stroke-linecap="round"/><circle cx="51" cy="32" r="5.5" fill="#e8743b"/></svg>
```

### 3.4 Type

- **Inter** (variable, weights 100 to 900) for text, **JetBrains Mono** (400, 500) for code, addresses, versions, eyebrows, numbers in tables. Both SIL OFL, self-hosted as woff2 (`/assets/fonts/inter-latin-wght-normal.woff2`), `font-display:swap`, the main font preloaded.
- DumbMonit's site and app use Geist and Geist Mono instead (SIL OFL, self-hosted). This is a legacy difference. **New projects use Inter and JetBrains Mono.**
- Body `.9375rem` (15 px), line height 1.6. Headings weight 600, `letter-spacing:-.02em`, line height 1.2, `text-wrap:balance`.
- `h1` hero: `clamp(2.125rem,1.4rem + 3vw,3.4rem)`, `letter-spacing:-.035em`, line height 1.08. Page `h1`: `clamp(1.75rem,1.3rem + 2vw,2.5rem)`. Section `h2`: `clamp(1.375rem,1.1rem + 1vw,1.75rem)`.
- Eyebrow (small label above a heading): JetBrains Mono `.6875rem`, weight 500, `letter-spacing:.06em`, uppercase, `--c-ink-3`.
- Lede: `1rem` to `1.125rem`, `--c-ink-2`, max width 36 to 44 rem.
- Exactly one `h1` per page.

### 3.5 Layout and spacing

- `.wrap`: `max-width:1160px`, `padding-inline:var(--gutter)`. Top bar, footer and hero grid may use 1280px.
- Sections: `.block{padding-block:48px;border-top:1px solid var(--c-line)}`, 72px from 900px. Alternate sections: `.block.alt{background:var(--c-surface)}`.
- Breakpoints: **600** (gutter 24, top bar buttons appear), **640 / 1000** (benefits 2 / 3 columns), **900** (split layouts, bigger paddings), **1100** (hero in two columns), **1140** (full nav, no burger).
- Radii: plate 6, button 8, card 12, demo 14, final box 16.
- Grid hero: the hero background is a 44 px square grid of `--c-line` hairlines plus a faint accent glow.

```css
.hero{padding-block:44px 56px;border-bottom:1px solid var(--c-line);
background:radial-gradient(48rem 26rem at 70% 10%,rgb(var(--accent-rgb) / .09),transparent 70%),
linear-gradient(var(--c-line) 1px,transparent 1px) 0 0 / 44px 44px,
linear-gradient(90deg,var(--c-line) 1px,transparent 1px) 0 0 / 44px 44px}
@media (min-width:900px){.hero{padding-block:80px 88px}}
```

### 3.6 Components

- **Button** `.btn`: `min-height:40px`, padding `0 16px`, radius 8, font `.875rem` weight 600, 16 px icon. `.btn-primary`: background `--c-primary`, text `--c-on-primary`. `.btn-secondary`: 1px `--c-line-strong` border on `--c-surface`. `.btn-lg`: `min-height:48px`. Primary action is **neutral (light), not the accent**. One primary per view.
- **Plate** `.plate`: status chip, `min-height:22px`, radius 6, `.75rem` weight 600, 13 px icon, always an icon plus a word. Variants `.plate-signal`, `.plate-info` (tint 12 to 13 percent, border 30 percent).
- **Panel** `.panel` (surface, 1px `--c-line-strong`, radius 12), **notice** `.notice` (advisory tint, icon, used for limits and warnings), **code block** `.code` with a copy button (`min-height:32px`, 40 on touch widths), **points**, **benefits** (icon in a 32 px square, h3, one sentence), **steps** (numbered, only when the order matters).
- Icons: 24 grid, `stroke-width:1.8`, round caps and joins, `currentColor`, inline SVG with `aria-hidden="true"`.
- Focus: `:focus-visible{outline:2px solid var(--c-ink);outline-offset:2px}`. Skip link first in `<body>`: `<a class="skip" href="#main">`.

### 3.7 Motion

- At most **one authored motion per page** besides the hero demo: the page-load rise and the scroll reveal count as the entrance, not extra.
- Durations: hover 200 ms, reveal 700 ms, hero rise 800 ms, rotating word 450 ms. Easing `cubic-bezier(.2,.7,.2,1)` or `--ease`. Nothing blinks or loops loudly. Entrance moves 18 to 20 px at most.
- Everything that moves is wrapped in `@media (prefers-reduced-motion:no-preference)`, and a reduce block turns off the rest:

```css
@media (prefers-reduced-motion:reduce){
*,*::before,*::after{transition-duration:.01ms!important;animation:none!important}
}
```

- JavaScript animations read `matchMedia('(prefers-reduced-motion: reduce)')` and do not start (the page then shows a still, usable frame). Pause when the tab is hidden or the element is off screen.
- Pages must read fully without JavaScript.

### 3.8 Accessibility

- Text contrast at least 4.5:1 (`--c-ink-3` on `--c-canvas` is the floor), large text and UI borders at least 3:1. Do not lighten `--c-ink-3`'s role, do not use it for anything that matters.
- **Status is never conveyed by colour alone**: icon plus word (plate), a label, a pattern.
- Tap targets at least **40 x 40 px** (44 for rows in a menu and for the mobile nav). Space between targets at least 6 px.
- **No horizontal overflow at 390 px.** Code wraps (`white-space:pre-wrap;overflow-wrap:anywhere`), grids use `minmax(0,1fr)`, `body{overflow-x:hidden}` is a safety net, not a fix. Check at 390 x 844 before shipping.
- Visible focus on everything, logical tab order, one `h1`, landmarks (`header`, `nav` with `aria-label`, `main#main`, `footer`), `alt=""` on decorative images, real text alternatives on informative ones, `lang` and `dir` on `<html>`.
- Toggles use `aria-pressed`, disclosure uses `aria-expanded` plus `aria-controls`, live regions use `aria-live="polite"`.
- Interactive demos are keyboard operable and have a Replay control.

## 4. Product site

Static HTML and CSS, a few kilobytes of JavaScript, generated by a build script from templates and one string file per language. English is the source.

### 4.1 Pages

| Path | Content |
|---|---|
| `/` | Home: hero, how it works (4 numbered steps), one honest limits block, final block with the quick start |
| `/features/` | Everything it does, grouped, and **what it does not do** |
| `/download/` | Install steps with copy buttons, requirements, versions and image names, `#support` block |
| `/demo/` | The static demo (see 4.9). Not generated by the site build |
| `/docs/` | The documentation (section 5). Not generated by the site build |
| `/404.html` | Logo, `404`, one sentence, button home, `noindex` |

Large products may add pages (DumbMonit has devices, roadmap, community). New projects start with the five above.

### 4.2 Top bar

Sticky, 52 px, `rgb(7 8 10 / .92)` with `backdrop-filter:blur(10px)`, bottom border `--c-line-strong`. Same structure on every site:

```html
<header class="topbar"><div class="wrap">
<a class="brand" href="/" aria-label="mccb home">[logo svg 28px]mccb</a>
<nav class="nav" id="site-nav" aria-label="Sections">
<a href="/features/">Features</a><a href="/download/">Download</a>
<a href="https://mccb.yety.ch/demo/">Demo</a><a href="https://mccb.yety.ch/docs/">Docs</a>
<a class="nav-extra" href="https://github.com/yetysw/mccb">GitHub</a>
<a class="nav-extra" href="/download/">Install</a>
</nav>
<div class="actions">
[language selector]
<a class="tb-btn" href="https://github.com/yetysw/mccb">[github icon]<span>GitHub</span></a>
<a class="tb-btn tb-primary" href="/download/">Install</a>
<button class="menu-btn" type="button" aria-expanded="false" aria-controls="site-nav" aria-label="Menu"><span aria-hidden="true"></span></button>
</div></div></header>
```

- Order: Features, Download, Demo, Docs; then GitHub and the primary **Install** button. `aria-current="page"` on the current link.
- From **1140 px** the nav is inline and the burger is hidden. Below, the burger opens a full-width list under the bar (links 44 px tall). `.nav-extra` links show only in that mobile list.
- `.tb-btn` buttons show from 600 px, 40 px tall below 1140, 36 px above. Language selector: a `<details class="lang">` with a globe icon and the short code (`EN`, `FR`), listing the nine languages by their own name, `aria-current="true"` on the active one.

### 4.3 Hero

```html
<section class="hero" id="top"><div class="wrap hero-grid"><div class="hero-text">
<div class="status-row"><span class="plate plate-signal">[check]MIT, no paid edition</span><span class="plate plate-info">[icon]Runs on your own machines</span></div>
<h1>Run it yourself. Share the <span class="rot"><span class="on">to-do list</span><span>backlog</span>…</span></h1>
<p class="lede">One or two sentences.</p>
<div class="cta"><a class="btn btn-primary btn-lg" href="/download/">Install</a><a class="btn btn-secondary btn-lg" href="/demo/">Try the demo</a><a class="btn btn-secondary btn-lg" href="/docs/">Read the docs</a></div>
</div>
<figure class="demo-fig">[interactive animation]</figure></div></section>
```

- Two plates: the licence plate (always "MIT, no paid edition") and one fact about where it runs.
- **Rotating word**: 3 to 5 words in the headline, all in one grid cell (`display:inline-grid`, every span `grid-area:1/1`) so width and height never move, colour `--accent-ink`, switch every 2.5 s with a 450 ms fade and a 0.6em slide. A screen reader gets the sentence with the first word. Without motion preference the first word stays.
- **Interactive animation** in a `.demo` frame (radius 14, bar with a mono title, tool buttons, a one-line `.d-note`). It plays by itself until the first click, tap or focus inside; then it belongs to the visitor and resumes after **20 s without input**. It is off screen or reduced-motion: still frame, still usable. It shows the product's real core idea in about five rows or lines, with fictional data, and has a Replay button.
- Desktop: copy left (5fr), demo right (6fr). Below 1100: stacked.

### 4.4 Footer and yety bar

Same on every site. The project row (brand, links), then one small line inside the same footer, with no border or background of its own: the yety logo, "A yety project" and "Discover all our projects", as a single link to the hub. Projects are not listed here: the hub lists them.

```html
<footer class="sh-foot"><div class="wrap">
<div class="sh-f-main"><a class="sh-f-brand" href="/">[logo 24]mccb</a>
<nav aria-label="Footer"><a href="/features/">Features</a><a href="/download/">Download</a><a href="https://mccb.yety.ch/demo/">Demo</a><a href="https://mccb.yety.ch/docs/">Docs</a><a href="https://github.com/yetysw/mccb">GitHub</a><a href="/download/#support">Support the project</a><a href="https://github.com/yetysw/mccb/blob/main/LICENSE">MIT licence</a></nav></div>
<div class="sh-f-bar"><a class="sh-home" href="https://open.yety.ch">[yety logo 18]<span>A <b>yety</b> project</span><span class="sh-all">Discover all our projects</span></a></div>
<p class="sh-note">Optional disclaimer line, 12px, --c-ink-3.</p>
</div></footer>
```

Links are 40 px tall, `14px` (last line `13px`). The hub (`open.yety.ch`) has no footer.

### 4.5 Support block

On `/download/#support`. Wording: "Every yety tool is free. If one saves you time, you can support its development." Then the primary button **Sponsor us on GitHub** (`https://github.com/sponsors/yetysw`). No other payment method.

### 4.6 Languages and URLs

- **Four locales**: `en` (source), `fr`, `de`, `it`. Docs may stay in English.
- URL scheme: English at the root (`/features/`), others under a prefix (`/fr/features/`, `/pt-BR/features/`, `/zh-Hans/`). `/docs/` and `/demo/` stay at the root.
- One string file per language, flat keys, `en.json` is the base, a missing key falls back to English, an unknown key stops the build. Do not rename keys.
- Translators: translate values only, keep HTML tags and placeholders (`{version}`), never translate product names, commands, ports, file names, code or `<code>` content. `*_meta_title` under about 70 characters, `*_meta_desc` under about 170, plain text. Keep every warning at full strength. Prefer an everyday word to a technical one when both are correct.
- First visit to the English root picks the language from `navigator.languages` (English when none of the four matches). The selector remembers an explicit choice.
- `<html lang="…" dir="ltr">` on each page.

### 4.7 SEO checklist

Every page, checked by the build (fail on any miss):

- [ ] `<title>` unique, pattern `<name> <page>: <what it gives>`, for example `mccb features: PST migration to IMAP, CalDAV and automix`. Home: `<name>: <one-line description>`.
- [ ] `<meta name="description">` unique, at most 170 characters.
- [ ] Exactly one `<h1>`.
- [ ] `<link rel="canonical">` with the absolute URL.
- [ ] `hreflang` for the nine codes plus `x-default` (English), the same list on every language version.
- [ ] Open Graph: `og:type`, `og:site_name`, `og:title`, `og:description`, `og:url`, `og:locale`, eight `og:locale:alternate`, `og:image` (`https://<name>.open.yety.ch/og.png`, 1200 x 630) with `og:image:alt`. Twitter: `summary_large_image` plus title, description, image, alt.
- [ ] JSON-LD in `<script type="application/ld+json">`: home is `SoftwareApplication` (`name`, `description`, `url`, `applicationCategory`, `operatingSystem: "Linux (Docker)"`, `isAccessibleForFree: true`, `license: https://opensource.org/licenses/MIT`, `offers` price `0`, `codeRepository`, `publisher` yety). Inner pages are `WebPage` with `isPartOf` the `WebSite` and `about` the software; the download page adds `softwareVersion` and `downloadUrl`.
- [ ] `sitemap.xml` lists every page with `lastmod` and the `xhtml:link` alternates for all languages. The docs add `/docs/sitemap-index.xml`, listed in `robots.txt`.
- [ ] `robots.txt`: everything allowed, crawlers of AI search and assistants are welcome and listed by name, `Sitemap:` lines.
- [ ] `llms.txt` ([llmstxt.org](https://llmstxt.org) format): `# name`, a `>` summary (what it is, how it runs, MIT), install in one sentence, then "Main pages" (home, features, download, demo, docs, support), "Source" (GitHub, releases, licence, yety hub), "Language versions", "Optional" (sitemap).
- [ ] Internal links and anchors resolve (the build checks them). `lang`, favicon, `apple-touch-icon`, `404.html`.

### 4.8 Security headers, cache, hosting

- Hosted on **Cloudflare Pages**, one Pages project per site named like the subdomain, deploying the built `dist/<site>` folder. The docs are copied into `dist/<site>/docs/` before deploying, so rebuild the site first.
- `_headers`:

```
/*
  X-Content-Type-Options: nosniff
  Referrer-Policy: strict-origin-when-cross-origin
  X-Frame-Options: DENY
  Content-Security-Policy: default-src 'self'; img-src 'self' data:; frame-ancestors 'none'; base-uri 'self'; form-action 'none'
/assets/*
  Cache-Control: public, max-age=31536000, immutable
```

- **No inline style or script.** The CSP forbids it. The build turns any `style="…"` into a generated class `u-<hash>` collected in the stylesheet.
- **Cache versioning**: `/assets/*` is immutable for one year, so the URL must change with the content: `site.css?v=<first 10 hex of the SHA-256 of CSS + JS>`, computed by the build and written into every page.
- One stylesheet (`site.css` = shared `product.css` + the project's accent file) and one script (`site.js`), both `defer`/blocking-free.
- `/docs/*` gets its own header block that removes the strict CSP and sets one that allows what the docs framework needs (inline scripts, WebAssembly search).

### 4.9 Static demo under `/demo/`

- A real front end running without a back end in the visitor's browser: the API is simulated in JavaScript (`fetch` and event streams mocked). No network call leaves the page, no service worker, no WebSocket.
- **Fictional data only**: documentation address ranges `192.0.2.0/24`, `198.51.100.0/24`, `203.0.113.0/24`, `example.com`, `*.home.arpa`, made-up names. No real hostname, IP, person or credential, in text or in screenshots.
- A visible badge "Demo, fictional data". Writes are accepted and forgotten on reload.
- Sits in the site's `dist/<site>/demo/` and carries its own `_headers` block that replaces the site CSP for `/demo/*`, as tight as the demo allows (start from `default-src 'self'; script-src 'self'; style-src 'self'; connect-src 'self'; object-src 'none'; frame-ancestors 'none'`, add only what a test shows is needed):

```
/demo/*
  ! Content-Security-Policy
  Content-Security-Policy: default-src 'self'; script-src 'self'; style-src 'self'; img-src 'self' data:; font-src 'self'; connect-src 'self'; media-src 'none'; object-src 'none'; base-uri 'self'; form-action 'self'; frame-ancestors 'none'
```

- **Deep links without `_redirects`**: the demo is a single page app with routes. Copy its `index.html` to `/demo/404.html`. Cloudflare Pages serves the nearest `404.html` for an unknown path, so `/demo/alerts/42` loads the app, which then reads the path. Do not add a `_redirects` file.
- Demo assets use a hashed folder or file names; the demo links back to the site and to the install page.

## 5. Documentation

- **Where**: `https://<name>.open.yety.ch/docs/`, in the same Pages project as the site. No Read the Docs, no separate domain.
- **Stack**: the shared docs kit, built on Starlight (Astro) with Pagefind search, tree on the left, table of contents on the right, dark and light themes, the project accent. The kit is written once; a project brings only a config and its sources.
- **Sources stay in the project repository** under `docs/` as plain Markdown, converted at deploy time (Sphinx/MyST, MkDocs or plain Markdown are all accepted). Translations use the suffix `page.fr.md` next to `page.md`, for the nine locales; the English page is the fallback.
- **Config** per project (`project.config.json`): `name`, `title`, `description`, `subdomain`, `repo` (`yetysw/<name>`), `accent` (`green`, `blue`, `violet`, `amber` or a `{dark, light}` object), `logo`, `lang`, `locales`, `source`.
- **Structure** (order of the sidebar):
  1. Home: what it is, a screenshot, three entry links (Install, first steps, the main concept).
  2. Get started: quick start, full installation, first device or first run, backups and restore.
  3. Using it: one page per task.
  4. Reference: configuration (every env variable with default), API, CLI, metrics, ports and paths.
  5. Security: what it protects, what it does not, how to verify images and releases.
  6. Operations: upgrading, troubleshooting, FAQ.
  7. Development: building, tests, contributing.
- **Tone**: same voice as section 1. Task titles are verbs ("Add a monitor"). Start a page with what the reader will have at the end. Commands are copyable blocks, one command per intent. State prerequisites, side effects and how to undo. Use admonitions (note, tip, warning) sparingly, always put limits in a warning. Every screenshot uses fictional data and has alt text.
- **Gates**: the build checks internal links, anchors, titles, descriptions, canonical and sitemap. A broken link fails the deploy. Each page has an "Edit this page" link to the repository.
- The UI and the site only **link** to the docs; the docs are not embedded.

## 6. App UI

The product UI is not the marketing site: it is where the work happens. DumbMonit (Svelte 5, Tailwind) and SuckerPot (React, Tailwind) are different stacks and visually close cousins. What they truly share, and the rule for new apps:

**Shared and required**

- **Dark first, calm, near-black ground.** Neutral surfaces, hairline borders, colour only where it means something. DumbMonit ground `#07080a`, SuckerPot `#0b0c0e`. No decorative gradients. New apps start from the tokens of section 3.1 (DumbMonit's "obsidian" theme: `html.obsidian` in `web/src/app.css`) and add a light theme only when users need it.
- **Tokens only.** Every colour comes from a CSS variable (`--c-*` in DumbMonit, `--bg`, `--surface`, `--border`, `--fg` in SuckerPot). No hex in components. Contrast of every token pair is tested (SuckerPot ships `contrast.test.ts`).
- **Density**: the app's base text is 13 px (DumbMonit body `.8125rem`, SuckerPot `sm` 13/20), tables and panels compact, line height at least 1.5.
- **Fonts**: Inter for UI, JetBrains Mono (or Geist Mono in DumbMonit) for addresses, hashes, commands, IDs and numbers in tables; tabular numbers. Self-hosted.
- **Status is never colour alone.** Icon plus word plus colour: DumbMonit `Plate` (`signal`, `info`, `advisory`, `warning`, `ghost`), SuckerPot severity (info, notice, warning, severe, each with its own icon). **Red is rare and means the worst case.**
- **Primary action is neutral** (the ink colour inverted), accent hues carry meaning, not branding.
- **Primitives** live in one folder (`web/src/lib/ui/` in DumbMonit, `web/src/components/ui/` in SuckerPot): Button, Panel/Card, Plate/Badge, EmptyState, ErrorNotice, Skeleton, Toast, Tabs, Field. Do not add one-off styles; extend a primitive.
- **Tap targets at least 40 px, no horizontal overflow at 390 px**, visible focus, keyboard reachable, `prefers-reduced-motion` turns every animation and tween off, one authored motion per page.
- **A sentence before data.** Page headers and cards open with one plain-language sentence that states what the data shows ("2 advisories, 1 unreachable.", "380 sessions from 265 addresses in the last 24 hours."). Numbers say what they count ("82 sessions").
- **Empty states are designed.** Keep the final layout, say what is missing in one sentence, offer one action (`EmptyState`: title, optional description, primary action). "Nothing needs you" is a result, not a hole.
- **Loading** uses skeletons with the same footprint as the final content, no spinner-only pages.
- **Error states** say what failed in words a sysadmin can act on, show the server's message when there is one, and offer retry or a way out (`ErrorNotice`). Config errors are shown, never silently swallowed. Never show a stack trace.
- **Times** are stored and sent in UTC, shown in the browser's zone, relative when recent with the absolute time on hover.
- **Everything is a link.** Filters live in the URL so a view can be shared.
- **Secrets never round-trip.** The API returns "has secret", never the secret; omitting a field on update keeps it.
- **Copy buttons** for every command, token and URL. A "mask addresses" mode for screenshots is welcome.

**Where projects truly differ**

| Topic | DumbMonit | SuckerPot | Rule for new apps |
|---|---|---|---|
| Framework | Svelte 5 (runes only) | React | Choose by team. Same tokens either way |
| Themes | Obsidian (dark default) plus a light console theme and public status pages | Dark and light, follows the system | Dark default; light optional, same token names |
| UI language | Nine locales with Paraglide | English only | **Nine locales** if the app is for end users (below); English only is acceptable for an expert tool, and then say so |
| Brand hue in the app | Status hues only | No brand hue, hues = sensor family | No brand hue in the app. The accent is for sites |
| Type | Geist and Geist Mono | Inter and JetBrains Mono | Inter and JetBrains Mono |

**i18n approach (DumbMonit, the model to copy)**

- Every visible string goes through the i18n layer (`m.<zone>_<component>_<meaning>()`, snake_case, for example `alerts_row_acknowledge`). No text in classes; generic components receive text through props.
- One key is one whole sentence with variables (`{count}`); never concatenate fragments; plurals, dates and numbers use the plural syntax or `Intl`; never put markup in messages.
- `web/messages/<locale>.json`, `en` is the base. A check fails when a locale misses a key or changes its `{variables}`. Texts that come from the server (catalogues, API errors) stay as served.
- Documentation and the demo may stay in English; say so in the link label.

## 7. Repository

Target state for every repository. DumbMonit is the model: <https://github.com/yety/dumbmonit>.

### 7.1 Files at the root

```
README.md  LICENSE  CONTRIBUTING.md  SECURITY.md  CHANGELOG.md
.github/CODEOWNERS  .github/dependabot.yml  .github/PULL_REQUEST_TEMPLATE.md
.github/ISSUE_TEMPLATE/{bug_report,feature_request}.yml  config.yml
.github/workflows/{ci,release,codeql,scorecard,security}.yml
docs/            (section 5)
docker-compose.yml  Dockerfile  .env.example
```

### 7.2 README

Every README has the same shape and stays short, about 150 lines at most: details belong in the docs, with a link. Use the same section names in this order, and the project name as written in section 2:

1. Centered header, in HTML, exactly this shape and nothing else in it:

```html
<div align="center">

<a href="https://<name>.open.yety.ch"><img src=".github/assets/banner.svg" alt="<name>: <tagline>" width="100%"></a>

<h3>One sentence that says what it is.</h3>


<br><br>

[CI badge] [OpenSSF Scorecard badge] [OpenSSF Best Practices badge, if the project has one] [MIT badge]

<br><br>

<img src="docs/assets/screenshot.png" alt="..." width="100%">

</div>
```

   Banner: `.github/assets/banner.svg`, 1280 x 280, ground `#07080a` with the 44 px grid, project logo at the left, the name, a short tagline, "a yety project" at the bottom right. Keep only the listed badges, in the default flat style: no language, test count, stack or version badges. 
2. **Overview**: 3 bullets. End with "Free, for good. MIT licence, no paid edition."
3. **Quick start**: Docker commands, first login, what to do next. Where to back up.
4. What it does / what it watches / features: concrete list.
5. Architecture in two or three lines.
6. **Limits** (or "Limits and disclaimer"), **Status** (alpha, what can still change).
7. **Contributing**: link to `CONTRIBUTING.md`, translations, `SECURITY.md`.
8. **License**: "MIT, see LICENSE", and the "as is" sentence.
9. **Support `<name>`**, last section:

```markdown
## Support <name>

<name> is free. If it saves you time, you can support its development:

[Sponsor us on GitHub](https://github.com/sponsors/yety), recurring or one-off.
```

### 7.3 Licence, contributing, security

- **LICENSE**: the standard MIT text. The copyright line names the organization or the handle (`Copyright (c) 2026 yety`), never a personal name or email.
- **CONTRIBUTING.md**: how to run everything in Docker (no host toolchain), dev setup, checks CI runs, branches (7.4), code and UI conventions, translations, the Developer Certificate of Origin (`git commit -s`), Conventional Commits, "one topic per PR", UI PRs include before and after screenshots, public repository hygiene (never commit secrets, captured data, real hostnames or IPs; use the documentation ranges).
- **SECURITY.md**: supported versions table (`main`/`edge` and latest tag yes, older no), report through GitHub private vulnerability reporting (`/security/advisories/new`), never a public issue, what to include, response times (acknowledge in 7 days, assessment in 14), disclosure and credit, scope, and how to verify releases. A public `abuse@` address may be listed only where the project handles abuse reports.
- **CODE_OF_CONDUCT.md** at the root (Contributor Covenant), as in DumbMonit.
- **CODEOWNERS**: `* @laupernoe @Theroxat` (both owners on everything).

### 7.4 Branches, pull requests, releases

- `main` is stable, `dev` is where work lands. Feature branches `feat/…`, `fix/…`, `docs/…`, `chore/…` open a PR **into `dev`**. `main` only receives `dev` through a PR. Never push directly to either.
- Rulesets: the default branch of every repository refuses deletion and force pushes and requires a pull request with one approval (stale approvals are dismissed). Where a `dev` branch exists it gets the same rules. Required status checks are added once a project's check names are stable, and tags `v*` can only be created by admins. Organization owners may bypass, so that the two of us can still ship alone; this is a deliberate choice and it lowers the Scorecard Branch-Protection and Code-Review results.
- One topic per PR, Conventional Commit title, template filled in (what, how, screenshots for UI, checklist). Merge when required checks are green and an owner approved.
- Every push to `dev` publishes the `:edge` image. A release is a `vX.Y.Z` tag on `main` after the owners agree: the workflow checks the tag against the version file, builds, signs, publishes the GitHub release with notes from `CHANGELOG.md`, and pushes `X.Y.Z`, `X.Y` and `latest`.
- Release assets carry checksums (`.sha256`) and Sigstore keyless signatures (`.sigstore.json`). Container images carry an SBOM (SPDX) and a SLSA build provenance attestation, pushed with the image to `ghcr.io/yetysw/<name>`. Verification:

```sh
gh attestation verify oci://ghcr.io/yetysw/<name>:<tag> -R yetysw/<name>
```

### 7.5 CI gates

Required status checks on both branches, always reporting (skipped steps still succeed): **build and test** for each language in the project (for DumbMonit: `Rust`, `Web UI`), and **Licences and advisories**. Typical content:

1. Formatter check and linter with warnings as errors (`cargo fmt --check`, `cargo clippy -- -D warnings`, `eslint`, `ruff`).
2. All tests, including the i18n key check and the UI type check.
3. Licence and advisory check (`cargo deny check licenses bans advisories`, or `licence-checker` and `npm audit`). Only OSI-approved licences pass.
4. Production build of the UI and of the Docker image (not pushed on PRs).
5. Docs build with warnings as errors.

Outside the gate: CodeQL, a weekly Trivy scan of the published images and an OSV scan of every lockfile, fuzzing of parsers that read outside input, coverage in the job summary.

### 7.6 Dependency pinning and updates

- **Every GitHub Action is pinned to a full commit SHA**, with the version in a trailing comment: `uses: actions/checkout@<40-hex> # v7.0.1`.
- Base images in Dockerfiles and tools run in CI are pinned by digest (`image:tag@sha256:…`).
- Lockfiles are committed (`Cargo.lock`, `package-lock.json` or `pnpm-lock.yaml`) and installs are frozen (`npm ci`, `--locked`).
- Workflow `permissions:` start at `contents: read`, widened per job only where needed. No `pull_request_target` with untrusted code.
- Dependabot (or Renovate) monthly for each ecosystem and for Actions, minor and patch grouped, majors reviewed by hand. Before choosing a version for a new dependency, read the latest release; never copy a version from memory.
- Secret scanning with push protection and Dependabot security updates are enabled.

### 7.7 OpenSSF goals

- **Best Practices**: every public repository earns the OpenSSF Best Practices badge (passing, then silver) and shows it in the README.
- **Scorecard**: `scorecard.yml` runs on push to `main`, weekly and on branch-protection changes, publishes results, and the badge is in the README. Aim for 8 or more out of 10. The checks that matter most here: Pinned-Dependencies, Token-Permissions, Branch-Protection, Code-Review, Signed-Releases, Dependency-Update-Tool, SAST, Security-Policy, Vulnerabilities, License, Fuzzing.

### 7.8 Sponsor button

Money goes through GitHub Sponsors: [github.com/sponsors/yetysw](https://github.com/sponsors/yetysw). Once the organization is accepted, every repository turns on *Settings > General > Features > Sponsorships* and inherits `.github/FUNDING.yml` from this repository.

## 8. New project checklist

In this order.

1. Pick a lowercase name; check `<name>.open.yety.ch`, `yetysw/<name>` and `ghcr.io/yetysw/<name>` are free.
2. Choose an accent (3.2) and draw the logo on the 64 grid (3.3).
3. Create the repository under `yetysw` with MIT licence, `dev` as the working branch, rulesets (7.4), security features on and the Sponsor button on (7.8).
4. Add the root files and `.github/` of 7.1, `CODEOWNERS` with both owners, README in the shape of 7.2, with its banner and the Support section.
5. Make it run with `docker compose up -d` from a published image; write `.env.example`; add CI (7.5) with pinned actions (7.6) and the release workflow with SBOM, provenance and signatures.
6. Write `docs/` and add the project config to the docs kit (section 5); check links.
7. Build the site: tokens, top bar, hero with plates and rotating word, interactive animation, features with "what it does not do", download with Support block, footer and yety bar, 404 (section 4).
8. Fill the nine string files; check titles, descriptions, hreflang, sitemap, `robots.txt`, `llms.txt`, JSON-LD (4.7).
9. Build the static demo with fictional data and its CSP (4.9).
10. Run the checks: 390 px without horizontal scroll, keyboard only, reduced motion, contrast, headers, no inline style, no external request.
11. Create the Cloudflare Pages project `<name>`, point `<name>.open.yety.ch` at it, deploy.
12. Add the project to the hub site, to the organization profile (`profile/README.md` in this repository, with its logo in `profile/assets/` and in the banner) and to the table in `SECURITY.md`.
13. Apply for the OpenSSF Best Practices badge, enable Scorecard, add both badges to the README.
14. Tag `v0.1.0` from `main` only when the owners agree.
