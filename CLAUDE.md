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

<!-- This section grows over time. Every session that makes meaningful changes
     should append what it learned. This is where compound value accrues.

     Good entries answer: What would the NEXT session need to know?
     - Decisions made and WHY (not just what changed — git log has that)
     - Things that are fragile or non-obvious
     - What was tried and didn't work (so nobody tries it again)
     - Patterns discovered in the data or the APIs
     - Gotchas that aren't obvious from reading the code

     Bad entries: "Updated foo.py" (that's a commit message, not knowledge) -->

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
