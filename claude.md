# Wombat Game Factory — Project Context

## Overview
A static portfolio website for **Dean Morris**, an independent board game designer based in London, UK. The brand is **Wombat Game Factory**. The site is hosted on **GitHub Pages** at `www.wombatgamefactory.com`.

The site serves two audiences:
1. **Publishers** — a professional pitch portfolio showing games available for licensing
2. **Playtesters** — can sign up via Mailchimp to be notified if a game gets published

---

## Tech Stack
- Plain **HTML / CSS** — no framework, no build step
- Hosted on **GitHub Pages**
- Assets (sell sheets, rulebooks) stored on **Google Drive** and linked
- Videos hosted on **YouTube** and embedded
- Newsletter signups via **Mailchimp** (one audience/list per game)
- Lightbox for photo galleries: **GLightbox** (loaded from CDN)

---

## File Structure
```
/
├── index.html              # Landing page
├── style.css               # Shared stylesheet (all pages)
├── games/
│   ├── acacia.html
│   ├── firefly-festival.html
│   ├── kentia.html
│   ├── superfan-convention.html
│   ├── highlands.html
│   ├── pacific-rails-inc.html
│   └── florence.html
└── assets/
    └── (logos, photos, etc.)
```

---

## Design System (style.css)

### CSS Variables
```css
--bg-dark         /* main page background */
--bg-card         /* card / panel background */
--border          /* subtle border colour */
--copper          /* primary accent (copper/bronze) */
--copper-light    /* lighter copper for hover states */
--cream           /* heading / label text */
--text            /* body text */
```

### Fonts
- **Oswald** — headings, labels, nav (loaded from Google Fonts)
- **DM Sans** — body text (loaded from Google Fonts)

### Key CSS Classes
- `.game-logo-column` — left column on game pages (logo + quick links)
- `.publisher-quick-links` — sidebar block with sell sheet / rulebook / video links
- `.quick-link` — individual link row inside `.publisher-quick-links`
- `.photos-grid-compact` — 4-column photo grid used on game pages
- `.video-compact` — constrained video embed (max ~460px wide)
- Status badges: `.badge-published`, `.badge-signed`, `.badge-in-development`

### Responsive
Mobile breakpoints are defined at the bottom of `style.css`. On mobile: photo grids collapse to 2 columns, video goes full width.

---

## Pages

### Landing Page (index.html)
- Wombat Game Factory logo at top
- Dean Morris bio, photo, contact details
- Game grid — all 7 games, each with: logo, name, status badge, one-line description
- Clicking a game card navigates to that game's page

### Game Pages (games/*.html)
Two-column layout:
- **Left column**: game logo + `.publisher-quick-links` block (sell sheet, rulebook, video)
- **Right column**: game name + tagline, stats bar, photo grid (GLightbox), video embed, description text

Each game page has a Mailchimp signup section ("Notify Me") at the bottom for playtest notifications.

Footer on every page: links to Instagram, YouTube, BoardGameGeek (Dean's designer profile).

---

## Games

| Game | Status | Notes |
|---|---|---|
| Pacific Rails Inc | Published | Link to BGG / publisher — no sell sheet needed |
| Florence | Published | Link to BGG / publisher — no sell sheet needed |
| Highlands | Signed | Cannot reveal details publicly; link to BGG entry only |
| Acacia | In Development | Full treatment — sell sheet, rulebook, photos, signup |
| Firefly Festival | In Development | Full treatment |
| Kentia | In Development | Full treatment |
| Superfan Convention | In Development | Full treatment |

---

## Mailchimp Integration
- One Mailchimp **audience per game** (In Development games only)
- Form uses a direct POST to Mailchimp's `list-manage.com` endpoint
- The form action URL format: `https://wombatgamefactory.usXX.list-manage.com/subscribe/post?u=XXXX&id=XXXX`
- Each game page has its own unique `u=` and `id=` values in the form action
- There is a hidden bot-trap field (`b_...`) that must be present and empty
- On submit the user stays on the page (no redirect)

---

## Conventions & Preferences
- All shared styles go in `style.css` — avoid inline `<style>` blocks in individual HTML files
- Use CSS variables for all colours — never hardcode hex values in HTML files
- GLightbox is initialised at the bottom of each game page with: `const lightbox = GLightbox({ touchNavigation: true, loop: true, autoplayVideos: false })`
- Footer is duplicated across pages (no server-side includes — this is a static site)
- Image assets use relative paths from the file's location (e.g. `../assets/acacia-logo.png`)

---

## External Accounts & Links
- **Domain**: `www.wombatgamefactory.com` (GitHub Pages custom domain, HTTPS enabled)
- **Email**: `hello@wombatgamefactory.com` (routed via Cloudflare Email Routing → personal Gmail)
- **GitHub**: Wombat Game Factory organisation account
- **Instagram**: instagram.com/wombatgamefactory
- **YouTube**: youtube.com/@wombatgamefactory
- **BGG designer profile**: boardgamegeek.com/boardgamedesigner/123443/dean-morris