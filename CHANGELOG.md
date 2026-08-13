# Changelog

All notable changes to Loan Manager are documented here.

This project follows a simple versioning scheme: `MAJOR.MINOR.PATCH`. Since this is a single-file app, "releases" are just tagged snapshots of `loan-manager.html`.

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
