# PKL Ranked — Parkour Legacy Leaderboard

An unofficial, community-maintained PARKOUR Legacy leaderboard and reference interface.

## Status

This repository is a working community prototype. Ranking data is provisional or unverified unless evidence is explicitly attached. The forum is a local browser demo: it does not synchronize, authenticate users, or send submissions to moderators.

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
- localStorage for browser-local edits and forum-demo posts;
- JSON import/export for transferring leaderboard data;
- installable web manifest and service worker.

The original snapshot remains available in the `parkour-leaderboard` directory on the `claude/parkour-leaderboard-site-5vyofn` branch of `deltadasher/Linux-stuff`.

Fan-made and not affiliated with PARKOUR, hudzell, Roblox, or Speedrun.com.
