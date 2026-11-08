# Card Games Page

- Goal: Move the card games off the home page onto a new secondary page, `card-games.html`, grouped as Literature Trick Takers, General Trick Takers, Family Games and Party Games. The home page keeps a Card Games group, which now holds three category tiles (Trick-Taking, Family, Party) linking into the new page.
- Created: 08/11/2026
- Run status: done
- Output location: s:\Dropbox\dev\Cardboard\github\wombatgamefactory.github.io (site root). New page: card-games.html. Edits: index.html, css/style.css, six game pages.

Decisions (Dean, 08/11/2026):
- Literature Trick Takers: Ahab and the Whale, Waltzing Matilda, Snowy River. General Trick Takers: Daruma Drama. Family Games: AI Wants You Dead. Party Games: Icebreaker.
- Icebreaker moves out of the home page Archive. Bucket List stays in Archive.
- Home page: three category tiles in the Card Games group, styled like game cards.
- Card game pages: breadcrumb becomes Home > Card Games > Game. The top nav "Games" link is unchanged.
- Workers don't commit. The manager commits locally after checking; nothing is pushed (pushing publishes the live site).

## Tasks

### T1 - Build card-games.html
- Status: done
- Depends on: -
- Worker: delegate-sonnet-medium
- Why this rung: a whole new page assembled from existing markup across several sections; needs care, not deep judgement.
- Brief: see dispatch prompt.
- Acceptance: card-games.html exists at site root; has the same head scripts (cookieyes, gtag, metricool), favicons and stylesheet as index.html with its own title/description/canonical/OG; nav and footer match index.html (nav links go to index.html#...); breadcrumb Home > Card Games; four groups in order with ids literature-trick-takers, general-trick-takers, family-games, party-games; the six cards are copied verbatim from index.html (image paths still valid from root); group counts correct; no inline style blocks or hardcoded hex; index.html untouched.
- Attempts: 1
- Result: card-games.html at root; six cards verified identical to index.html by script; no CSS needed (html scroll-padding-top: 90px already covers anchors).

### T2 - Home page: category tiles, remove moved cards
- Status: done
- Depends on: T1
- Worker: delegate-sonnet-medium
- Why this rung: edits to index.html plus new tile styling in style.css that must sit with the existing design system.
- Brief: see dispatch prompt.
- Acceptance: the five card game cards are gone from index.html; the Card Games group holds three tiles linking to card-games.html#literature-trick-takers, #family-games, #party-games; Icebreaker removed from Archive and Archive count reads 2 titles; Card Games count reflects categories sensibly; new CSS in css/style.css only, uses variables, works at mobile width; nothing else on the page changed.
- Attempts: 1
- Result: three suit-glyph category tiles plus "View all card games" header link; Archive 2 titles; diff confined to the two groups; manager rendered at 375px and 1300px with Playwright (no horizontal scroll, anchors clear the sticky nav); committed 37d8b53.

### T3 - Breadcrumbs on the six card game pages
- Status: done
- Depends on: T1
- Worker: delegate-haiku
- Why this rung: identical mechanical edit across six files.
- Brief: see dispatch prompt.
- Acceptance: in ahab-and-the-whale, waltzing-matilda, snowy-river, daruma-drama, ai-wants-you-dead and icebreaker, the breadcrumb's middle link reads "Card Games" and points to ../card-games.html#<that game's section id>; nothing else in those files changed (git diff shows one line changed per file, or two if the text and href are on one line).
- Attempts: 1
- Result: six breadcrumb lines changed, diff verified, top nav untouched; committed 4f4ea12.

## Log
- 08/11/2026 - Plan written; awaiting approval.
- 08/11/2026 - Approved by Dean. T1 launched (delegate-sonnet-medium).
- 08/11/2026 - T1 checked and passed; committed. T2 (delegate-sonnet-medium) and T3 (delegate-haiku) launched in parallel.
- 08/11/2026 - T3 checked and passed; committed 4f4ea12.
- 08/11/2026 - T2 checked and passed (own render at phone and desktop width); committed 37d8b53. CLAUDE.md updated with the new page and how to add future card games.
- 08/11/2026 - Run done. Outcome: 3 tasks, all passed first time, no escalation. Lessons: the worker's own headless-Chrome mobile render was unreliable (window can't go below ~500px); Playwright with a 375px viewport works on this PC. Nothing pushed.
