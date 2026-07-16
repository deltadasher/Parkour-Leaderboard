# AGENTS.md — PKL Ranked

This file gives ChatGPT, Codex, Claude Code, and other coding agents enough context to work on this project without inventing requirements or misrepresenting placeholder data.

## Project purpose

PKL Ranked is an unofficial, community-maintained leaderboard and discussion hub for **PARKOUR Legacy**.

Current sections:

- Leaderboards
- Per-item rankings
- Forum
- Announcements
- Rulebook

Current leaderboard categories:

- Overall (derived view)
- Meta
- Recounter
- Gearless
- Gearless: Gloveless
- Time Trials

The site is fan-made and is not affiliated with PARKOUR, hudzell, Roblox, or Speedrun.com.

## Repository location

Project directory:

```text
parkour-leaderboard/
```

Primary files:

```text
parkour-leaderboard/index.html
parkour-leaderboard/README.md
parkour-leaderboard/AGENTS.md
```

## Current architecture

The project is currently a static, dependency-free application contained primarily in `index.html`.

It uses:

- HTML
- CSS
- vanilla JavaScript
- hash routing
- `localStorage`
- JSON import/export
- no build system
- no package manager
- no backend
- no database

Routes currently include:

```text
#/ranked
#/items
#/forum
#/announcements
#/rules
```

Preserve the ability to open the project directly in a browser unless the user explicitly approves a larger architectural migration.

## Data model

Leaderboard data is stored in the JavaScript `BUILTIN` object inside `index.html`.

Each category generally contains:

```js
{
  label: "Meta",
  unit: "pts",
  desc: "Category description",
  gear: ["Optional", "gear", "list"],
  players: [
    {
      name: "RobloxUsername",
      pts: 1234,
      note: "Optional note"
    }
  ]
}
```

Player order determines leaderboard placement unless the application explicitly implements a different sorting system.

Do not silently reorder real or provisional player data.

The Overall board is a derived, non-editable view. Its score is calculated from 70% of a player's
average Review Score across Meta, Recounter, Gearless, and Gearless: Gloveless; up to 15 points from
average placement strength across those represented boards, scaling linearly from 15 points for #1
to 0.30 for #50; 2.5 points per ranked category represented, capped at 10; and 1 point per
evidence-qualified item review, capped at 5. Time Trials must remain excluded from Overall because
its in-game score is not on the 0–100 scale.

## Competitive ranks and per-item reviews

The competitive rank order is:

```text
Unranked, Bronze, Silver, Gold, Platinum, Diamond, Master, Elite
```

The project owner confirmed that every player in the top 50 of Meta, Recounter, Gearless, and
Gearless: Gloveless is Elite. Keep competitive rank separate from leaderboard placement, tier/placement
band, and Review Score. Time Trials does not use these competitive ranks.

Per-item lists are evidence-qualified and intentionally variable in length. Do not infer that every
top-50 player has used every item, and never pad a per-item list to 50. The current rubric totals 100:
proficiency 30, gap impact 25, tactical application 15, routing and integration 15, adaptability 10,
and results 5. The owner specifically confirmed ncm_k's leading Wingsuit, Aero Punch, and Thrust
Capacitor performance and excluded ncm_k from Springhook pending qualifying current-season evidence.

Player profile bios are deliberately unserious first-person community flavor text. They should read
like jokes, introductions, nonsense, or something a player might put in a casual profile—not as a
competitive resume. Do not insert placements, scores, item reviews, or evidence summaries into the bio;
those already appear elsewhere in the card. Never describe flavor bios as authenticated player quotes.
Do not invent demographics, locations, relationships, biographical history, or real-world claims.

## Meta category

Meta currently concerns combined proficiency with:

- Wingsuit
- Aero Punch
- Thrust Capacitor
- Springhook

The intended evaluation model considers:

- individual gear proficiency;
- gear integration;
- match impact;
- adaptability;
- competitive results;
- opponent quality;
- evidence integrity.

Each required gear must be used meaningfully at least three times during a qualifying session.

Do not describe Meta merely as “anything goes.” A more accurate description is:

> Combined mastery of Wingsuit, Aero Punch, Thrust Capacitor, and Springhook under standard ranked rules.

## Tier model

The intended tiers are:

- S
- A
- B
- C

Tiers should represent evaluated proficiency, not automatically correspond to fixed placement ranges.

Do not assume:

```text
S = ranks 1–10
A = ranks 11–20
B = ranks 21–35
C = ranks 36–50
```

unless the project owner explicitly chooses placement bands instead of evaluation grades.

A player may rank highly without qualifying for S tier, and multiple players may share a tier while retaining distinct numerical placements.

## Evidence and verification

The leaderboard should distinguish between:

- verified data;
- provisional data;
- nominations;
- archived data.

Never present generated point totals or placeholder placements as verified community facts.

Preferred evidence includes:

- full uncut ranked-session recordings;
- official match logs;
- server-side replays;
- tournament VODs;
- moderator-recorded matches.

Highlight compilations alone are not sufficient for full verification.

## Important truthfulness rules

Do not claim that:

- moderation ratified rules unless actual moderators did so;
- dates are official unless supplied or approved by the project owner;
- generated rankings are real community rankings;
- a local-only forum is a functioning shared community forum;
- a player owns a particular Roblox account without evidence;
- Speedrun.com names necessarily match Roblox usernames.

Use explicit labels such as:

- Draft
- Provisional
- Unverified
- Archived

when appropriate.

## Forum status

The built-in forum threads are preserved community archives, as confirmed by the project owner. Do
not relabel them as examples, samples, or fabricated demo content. Do not silently rewrite their
substance; terminology corrections should be narrowly sourced to current PARKOUR Legacy mechanics.

New forum threads and replies are public GitHub Issues and comments. GitHub supplies account login,
identity, persistence, notifications, moderation history, and abuse controls. The static site reads
matching public issues from GitHub's unauthenticated REST API and links to GitHub for posting or replying.
The built-in historical threads remain a read-only archive.

Fictional forum seeds are stored separately in `SEEDED_FORUM_THREADS` and
`SEEDED_FORUM_REPLIES`, carry a visible `seeded prototype` label, and are not community records.
`FORUM_CHARACTERS` contains the owner-supplied ncm_k and AstrMotif definitions plus stable,
deterministically generated personas for every seeded player. Do not describe these personas or
seed posts as authenticated statements by the named players.

`HIGHLIGHT_SEEDS` supplies the fictional Game Highlights board. Its 25 threads are a dated snapshot:
five each for AstrMotif, hi_4v, bn7t, Prezerf, and PlanetOfEnder, the built-in Overall top five when
authored on 2026-07-16. Keep the highlight threads and replies visibly fictional/local-only; do not
claim that the described clips or quoted reactions are authenticated player statements.

This means:

- new posts are shared publicly and synchronized between devices;
- a GitHub account is required to post or reply;
- authentication secrets never enter the static site;
- GitHub usernames identify public authors, but do not prove ownership of similarly named Roblox accounts;
- public API rate limits or network failures may temporarily hide the live listing, while direct GitHub links remain available.

Do not add a password form, token input, or fake authentication layer to the static site. Do not restore
the old localStorage forum composer. Keep repository-managed announcements separate from forum posts.

Do not imply that locally submitted appeals or leaderboard applications reach staff.

## Announcements status

Announcements should include:

- title;
- type;
- publication date;
- effective date when applicable;
- status;
- author;
- affected categories;
- required player action;
- revision history when revised.

Supported status labels may include:

- Draft
- Upcoming
- Active
- Revised
- Archived
- Emergency

Exact dates are preferred over vague wording such as “soon.”

Do not fabricate official publication or effective dates.

## Rulebook status

The project owner confirmed ratification on 2026-07-14 for the Meta, Recounter, Gearless, and
Gearless: Gloveless rulebooks. Treat version 1.1 and the shared six-round gap-monitoring model as
ratified until the owner explicitly revises or withdraws that status.

The public interface should ideally provide:

1. a concise qualification summary;
2. scoring criteria;
3. evidence rules;
4. prohibited conduct;
5. appeals;
6. a link or expandable area for the complete rules.

Avoid forcing ordinary users to read the full long-form rulebook before understanding the category.

## Design direction

Preserve the current visual identity unless asked to redesign it:

- strong display typography;
- compact leaderboard presentation;
- category accent colors;
- dark/light theme support;
- responsive mobile layout;
- prominent top-three presentation;
- readable long-form rules;
- restrained industrial/parkour visual language.

Avoid generic corporate dashboard styling.

Maintain:

- keyboard accessibility;
- visible focus states;
- semantic headings;
- reduced-motion support;
- sufficient contrast;
- usable mobile controls.

## Editing constraints

When changing the project:

1. Inspect the full relevant section before editing.
2. Make the smallest coherent change.
3. Preserve existing localStorage data compatibility where practical.
4. Avoid introducing dependencies for trivial features.
5. Do not replace real usernames or rankings without explicit instruction.
6. Do not invent community disputes, staff members, rulings, or player biographies.
7. Keep fan-made and non-affiliation notices visible.
8. Test all hash routes after navigation changes.
9. Test direct page loads and browser back/forward navigation.
10. Test both light and dark themes.
11. Test narrow mobile widths.
12. Update the README when behavior or architecture changes.

## Safe content categories

Agents may freely improve:

- layout;
- accessibility;
- routing;
- search;
- filters;
- import/export validation;
- local data handling;
- rulebook navigation;
- announcement presentation;
- provisional labels;
- submission templates;
- code organization;
- documentation.

Agents should ask or clearly flag assumptions before changing:

- actual player rankings;
- official points;
- moderation decisions;
- punishment lengths;
- eligibility thresholds;
- gear definitions;
- season dates;
- staff identities;
- verified Roblox usernames.

## Recommended near-term work

High-priority improvements:

1. Mark provisional ranking evaluations clearly.
2. Keep read-only archived threads distinct from live public GitHub threads.
3. Preserve the ratified status of all four category rulebooks unless the project owner changes it.
4. Preserve archived publication/effective dates unless the owner supplies a correction.
5. Decouple tier grades from automatic rank bands.
6. Replace “anything goes” in the Meta description.
7. Add per-player verification status.
8. Add category-specific eligibility summaries.
9. Add robust JSON schema validation during imports.
10. Add a clear path for a future shared backend.

## Future backend guidance

A real shared forum and submission system will require:

- authentication;
- persistent storage;
- authorization roles;
- server-side validation;
- rate limiting;
- moderation logs;
- evidence-link storage;
- audit history;
- backups;
- privacy and abuse controls.

Do not bolt a fake authentication UI onto localStorage and call it secure.

When a backend migration is approved, prefer separating:

```text
data
presentation
routing
storage
validation
moderation logic
```

rather than continuing to expand one monolithic HTML file indefinitely.

## Validation checklist

Before completing a change, verify:

```text
[ ] Leaderboard route loads
[ ] Forum route loads
[ ] Announcements route loads
[ ] Rulebook route loads
[ ] Browser back and forward work
[ ] Search still works
[ ] Edit mode still works
[ ] Import/export still works
[ ] Existing localStorage data does not crash the page
[ ] Mobile layout remains usable
[ ] Light and dark themes remain readable
[ ] Placeholder content is labeled honestly
[ ] No unsupported claims were added
```

## Project-owner intent

The goal is to build a credible top-50 ranked-mode resource once PARKOUR Legacy ranked play becomes established.

The project should prioritize:

- evidence over popularity;
- transparent criteria;
- honest provisional labels;
- reproducible review;
- resistance to farming, boosting, and staged evidence;
- a useful community interface without pretending unfinished infrastructure is already operational.
