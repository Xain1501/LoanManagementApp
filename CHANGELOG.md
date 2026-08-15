# Changelog

All notable changes to Loan Manager are documented here.

This project follows a simple versioning scheme: `MAJOR.MINOR.PATCH`. Since this is a single-file app, "releases" are just tagged snapshots of `loan-manager.html`.

---

## [1.5.0] — Partial payments

### Changed
- **Replaced "Mark Settled" with per-entry partial payments.** The binary settled/unsettled toggle didn't reflect real repayment — loans are often paid back in chunks, not all at once.
- Every entry now tracks a list of payments logged against it. An entry's **remaining balance** = original amount − sum of its payments, and this is what now feeds every total (overall summary, People view, person detail).
- An entry **automatically becomes "Settled"** once its remaining balance hits 0 — no manual action needed. It stays visible in history (dimmed, struck-through, tagged) the same as before.
- Entries with an outstanding balance show a progress bar and "PKR X of Y paid" once at least one payment has been logged.
- Tap **"Add Payment"** on any entry to log a partial or full payment (amount + date). Tap **"View payments"** to see and remove individual payments logged against that entry.

### Migration
- Existing data from any prior version upgrades automatically — no action required. A previously "Settled" entry becomes fully paid (remaining 0); a previously unsettled entry keeps its full outstanding balance. This applies both to data already in your browser and to any old backup file you import.

---

## [1.3.0] — Quick actions & import hardening

### Added
- Quick-add (**+**) button on each person card in the People view, pre-fills their name in the entry modal for faster repeat entries
- Search-by-name on both the Entries and People views
- Sort control for entries: newest/oldest, amount high–low/low–high, name A–Z
- "Mark Settled" action per entry — excludes it from all totals while keeping it visible in history (dimmed, struck-through, tagged "Settled")
- Comma-formatted input mask for PKR amounts while typing

### Changed
- Import now normalizes entries from **any** prior export format (bare array, wrapped object without `archived`, or the current schema) so old backups always import without errors
- Archive status is now included in exports and restored on import (previously only entries were saved)

> **Note (superseded in 1.5.0):** the "Mark Settled" toggle described above was replaced by partial payments in v1.5.0 — see above.

---

## [1.2.0] — People view & archiving

### Added
- **People view**: per-person payable / receivable / net summary cards, sorted alphabetically
- Tap into a person for their full transaction history with descriptions and dates
- Archive a person once their net balance is exactly 0 — hides them from the active list without deleting their history
- Auto-unarchive: if new activity is logged for an archived person, they automatically return to the active list
- Archived / Active sub-tabs within the People view

---

## [1.1.0] — Backup & data safety

### Added
- **Export**: saves all entries to a real, timestamped `.json` file in the device's Downloads folder
- **Import**: restores from a backup file, with a choice to merge with or replace current data
- Backup reminder banner — appears if no export has been made in 7+ days

### Why
Browser local storage can be cleared by the OS or by clearing site data. Export/Import makes data portable and safe independent of the browser cache.

---

## [1.0.0] — Initial release

### Added
- Add unlimited people, each entry marked **Payable** (you owe them) or **Receivable** (they owe you)
- PKR amounts, description, and date on every entry
- Running totals: total payable, total receivable, net balance
- Single-file, dependency-free HTML app — no build step, no backend, works fully offline
- Installable on Android via home-screen shortcut (through Chrome's Share menu or a file-manager shortcut, since the app is a local file)
