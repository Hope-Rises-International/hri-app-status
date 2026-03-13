# Claude Code — Project Instructions

## About this project

**HRI Project Status Dashboard** — A single-page HTML dashboard that displays real-time status of all HRI Claude AI build projects. Reads from the Project Status Tracker spreadsheet (Sheet ID: `1KD7Zds9WlIQRubD2z7r2SmcTIWbIQCQtkfE713P88Ng`) via the Sheets Bridge `readAll` API.

- **Stack:** Single-file HTML + CSS + vanilla JS (no build step)
- **Data source:** Sheets Bridge API (`readAll` mode)
- **Hosting:** GitHub Pages
- **Launch point:** HRI Internal Portal (Data & Integration section)
- **Start date:** 2026-02-27 (day count displayed on dashboard)

## Stack Learnings (canonical source)

Stack-level learnings live in ONE place:
- Repo: `Hope-Rises-International/hri-template-repository`
- File: `hri-stack-learnings.md`
- Read before any infrastructure, auth, deployment, or tooling work.
- Update directly via GitHub API when you discover a stack-level gotcha. See session-end protocol below.

Do NOT create a local `learnings.md` or `hri-stack-learnings.md` in this repo. If one exists, merge any unique content upstream and delete the local copy.

## Project knowledge

**[2026-03-13 | Bill | Initial dashboard build]**
- **Decided:** GitHub Pages hosting (not Apps Script) because the dashboard is read-only HTML with no server-side logic or domain restriction needed. Simpler deploy model (push to main) vs clasp ceremony. Can migrate to Apps Script later if domain restriction becomes necessary.
- **Decided:** Data fetched live from Sheets Bridge `readAll` mode on each page load. For 12-15 rows this is instant. The API key is exposed in client-side JS — acceptable because the bridge is read/write but the key is already shared across all HRI repos.
- **Changed:** Dashboard live at `https://hope-rises-international.github.io/hri-app-status/`. Added as tool card in Internal Portal (Data & Integration section, badge-live).
- **Watch out:** The `fetch()` call uses `Content-Type: text/plain` (not `application/json`) to avoid CORS preflight on the Apps Script endpoint. If this stops working, check CORS behavior on the Sheets Bridge.
- **Watch out:** The Sheets Bridge endpoint requires `ANYONE_ANONYMOUS` access in `appsscript.json` for browser-based fetch calls to work. If the bridge is redeployed with `ANYONE`, the dashboard will break with 401.

---

## Session Start

Before beginning work, check the most recent Project Knowledge entry below. If it contains an "Open" field, surface the open items to the user and confirm whether to continue that work or start something new.

---

## Session-End Protocol

**The full protocol lives in one place:** `session-end-protocol.md` in `hri-template-repository`.

At session close, fetch and follow it:

```bash
gh api /repos/Hope-Rises-International/hri-template-repository/contents/session-end-protocol.md \
  --jq '.content' | base64 -d > /tmp/session-end-protocol.md
```

Then read `/tmp/session-end-protocol.md` and execute all steps.

This ensures every repo uses the latest protocol without needing per-repo updates.
