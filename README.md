# PKL Ranked — Parkour Legacy Leaderboard

An unofficial, community-maintained PARKOUR Legacy leaderboard and reference interface.

## Status

This repository is a working community leaderboard. The ratified rulebook covers **Meta, Recounter, Gearless, and Gearless: Gloveless**, each with its own equipment rules and 100-point weighting. The four ranked boards display provisional Review Scores summarizing current-season performance; exact in-game Ranked Ratings have not yet been published. A derived **Overall** board combines ranked-score average, average board-placement strength, category breadth, and per-item evidence depth. Review Scores use hundredths and share role-specific runner-gap and catcher-follow monitoring. Every listed top-50 player on those four boards has the competitive rank **Elite**; Time Trials retains its in-game point system and does not use competitive ranks.

Leaderboard entries can also carry an **Under Review** status without being removed or treated as a cheating finding. Current integrity notices and unresolved appeals are recorded separately from confirmed moderation decisions.

The Per-item page contains evidence-qualified, variable-length rankings for all 14 tracked items. Its 100-point Review Score weights proficiency, gap impact, tactical application, routing and integration, adaptability, and results. Archived forum threads are preserved as community records. Separate fictional, local-only prototype seeds demonstrate chaotic forum activity, including a 25-thread Game Highlights board with five threads for each player in the built-in Overall top-five snapshot; they are visibly labeled and never mixed with user-created posts. New public threads and replies use GitHub Issues, with GitHub accounts providing login, identity, notifications, and moderation history. The site reads current public threads through GitHub's public API.

## Run locally

Open `index.html` directly, or serve the directory with any static file server. No build step or package installation is required.

## Install as a desktop-style app

When hosted over HTTPS, supported browsers can install the site as a Progressive Web App. The service worker caches the application shell for repeat visits and basic offline use.

## GitHub Pages

The workflow in `.github/workflows/pages.yml` publishes the repository root whenever `main` changes. In repository **Settings → Pages**, set the source to **GitHub Actions**.

Expected URL: `https://deltadasher.github.io/Parkour-Leaderboard/`

## Architecture

- dependency-free HTML, CSS, and vanilla JavaScript;
- hash routes for leaderboards, per-item reviews, forum archives, announcements, and rulebooks;
- localStorage for browser-local leaderboard edits;
- live public forum listings from GitHub Issues, with posting and replies handled securely by GitHub;
- deterministic forum-character personas for every seeded player, plus separately stored fictional prototype threads and replies;
- persistent Auto/Dark/Light theme control and reduced-motion-aware interface animation;
- click-to-open player profile cards with unserious first-person bios, board placements, per-item reviews, notes, and archived forum activity for any listed player;
- GitHub Issue forms for persistent submissions, appeals, rule proposals, discussion, and reviewed announcement requests;
- JSON import/export for transferring leaderboard data;
- installable web manifest and service worker.

The original snapshot remains available in the `parkour-leaderboard` directory on the `claude/parkour-leaderboard-site-5vyofn` branch of `deltadasher/Linux-stuff`.

Fan-made and not affiliated with PARKOUR, hudzell, Roblox, or Speedrun.com.
