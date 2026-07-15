# PKL Ranked — Parkour Legacy Leaderboard

An unofficial, community-maintained PARKOUR Legacy leaderboard and reference interface.

## Status

This repository is a working community prototype. The four ranked boards display provisional **0–100 Review Scores** summarizing current-season performance; exact in-game **Ranked Ratings** have not yet been published. Time Trials retains its in-game point system. Built-in forum threads are example data; local drafts use browser storage, while persistent community intake uses GitHub Issue forms.

## Run locally

Open `index.html` directly, or serve the directory with any static file server. No build step or package installation is required.

## Install as a desktop-style app

When hosted over HTTPS, supported browsers can install the site as a Progressive Web App. The service worker caches the application shell for repeat visits and basic offline use.

## GitHub Pages

The workflow in `.github/workflows/pages.yml` publishes the repository root whenever `main` changes. In repository **Settings → Pages**, set the source to **GitHub Actions**.

Expected URL: `https://deltadasher.github.io/Parkour-Leaderboard/`

## Architecture

- dependency-free HTML, CSS, and vanilla JavaScript;
- hash routes for leaderboard, forum demo, announcements, and rulebook;
- localStorage for browser-local edits and forum drafts;
- GitHub Issue forms for persistent submissions, appeals, rule proposals, discussion, and reviewed announcement requests;
- JSON import/export for transferring leaderboard data;
- installable web manifest and service worker.

The original snapshot remains available in the `parkour-leaderboard` directory on the `claude/parkour-leaderboard-site-5vyofn` branch of `deltadasher/Linux-stuff`.

Fan-made and not affiliated with PARKOUR, hudzell, Roblox, or Speedrun.com.
