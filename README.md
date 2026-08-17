# 🎯 jobhunter

An auto-refreshing tracker for remote job hunting — one spreadsheet, one daily scrape, zero manual board-hopping.

A scheduled agent scans a set of remote job boards every day, keeps only postings from the **last 3 days**, filters out anything that matches a growing list of disqualifiers, skips duplicates, and appends whatever's left to the tracker below.

## 📊 Snapshot

| Metric | Count |
|---|---|
| Total listings tracked | 35 |
| 🟢 High priority | 3 |
| 🟡 Medium priority | 23 |
| ⚪ Low priority | 9 |
| ✅ Applied | 9 |
| 🎤 Interviews | 0 |
| 💼 Offers | 0 |
| 📋 Still to review | 26 |

**By role bucket:** TAM (6) · Customer Success (9) · Solution Consultant (11) · Application Support (9)

*(Snapshot as of 2026-08-17 — the live numbers are always in [`Remote_Job_Search_Tracker.xlsx`](./Remote_Job_Search_Tracker.xlsx) → `Dashboard` tab.)*

## 📁 What's in the file

The tracker (`Remote_Job_Search_Tracker.xlsx`) has three tabs:

- **`Job Tracker`** — one row per listing: title, company, remote scope, salary (as listed), priority, source board, dates, URL, status, and notes.
- **`Dashboard`** — auto-summarized counts by status and role bucket.
- **`How To Use`** — the rules the scraper follows, including the current exclusion list.

## 🔄 How the daily refresh works

1. Reads the `Notes` column for anything you've flagged as a disqualifier (a region lock, a language requirement, a closed listing, etc.) and folds it into the exclusion rules.
2. Searches the job boards for new postings dated within the **last 3 days only**.
3. Cross-checks candidates against existing rows by company + title and by URL — no duplicates.
4. Drops anything matching an exclusion rule.
5. Appends whatever's left, updates the dashboard counts, and commits.

**Flag a bad match once in `Notes` and it won't come back on future runs.**

## ✋ Using it day to day

- Update `Status` as you go: `To Review` / `Applied` / `Interview` / `Offer` / `Rejected` / `Not Pursuing`.
- Fill in `Date Applied` and `Notes` as you work through listings — Notes doubles as the exclusion-rule feed for the scraper.
- `Suggested CV` tells you which resume version fits: `TAM` / `CS` / `APE`.

---
*Maintained by a scheduled Claude Code agent. Personal identifying details (name, exact target salary, home location) are kept out of this public copy — see the `How To Use` tab for the general rules.*
