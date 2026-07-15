# AGENTS.md — PKL Ranked

This file gives ChatGPT, Codex, Claude Code, and other coding agents enough context to work on this project without inventing requirements or misrepresenting placeholder data.

## Project purpose

PKL Ranked is an unofficial, community-maintained leaderboard and discussion hub for **PARKOUR Legacy**.

Current sections:

- Leaderboards
- Forum
- Announcements
- Rulebook

Current leaderboard categories:

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
- sample or placeholder data;
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
- Sample Data
- Local Demo
- Archived

when appropriate.

## Forum status

The current forum stores user-created threads and replies in that browser’s `localStorage`.

This means:

- posts are not shared between users;
- posts are not synchronized between devices;
- clearing site data removes local posts;
- there is no authentication;
- there is no real moderation system;
- usernames are not identity-verified.

Until a backend exists, visibly identify it as a local forum prototype or demo.

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

The rulebook is a working community draft unless the project owner explicitly confirms ratification.

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

1. Mark placeholder and provisional ranking data clearly.
2. Change the forum label to indicate that it is currently local-only.
3. Mark the rulebook as a draft unless ratification is confirmed.
4. Remove fabricated publication/effective dates or label them as examples.
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
