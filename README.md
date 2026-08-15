# Loan Manager

**A single-file, zero-dependency loan tracker for PKR payables and receivables.**

No installs. No backend. No frameworks. No build step. Just one `.html` file you open in a browser — on desktop or Android — and it works.

---

## Why it exists

Most "expense tracker" apps are bloated: accounts, ads, cloud sync you didn't ask for, and megabytes of JavaScript for something that's really just a list with a plus/minus sign. This project is the opposite bet — **do one job well, stay under a few hundred KB, and never grow past what fits in a single file.**

## What it does

- Track **unlimited people** and their loans
- Every entry is marked **Payable** (you owe them) or **Receivable** (they owe you)
- Amounts in **PKR**, with description + date on every entry
- **Partial payments** — log a payment against any specific entry; its remaining balance updates automatically, and it settles itself once fully paid. No manual "mark as settled" needed.
- **People view** — see every person's payable / receivable / net at a glance, tap in for their full history
- **Search & sort** — find any entry or person by name, sort entries by date, amount, or name
- **Archive** people once their net balance hits zero, without losing their history
- **Export / Import** — one-tap backup to a real `.json` file on your device, and restore it anytime — old backups always import cleanly, even from earlier versions
- All data lives in your browser's local storage — nothing leaves your device, ever

## How to use it

1. Download `loan-manager.html`
2. Open it in Chrome (or any modern browser)
3. *(Optional, Android)* Long-press the file in your file manager → **Add shortcut to Home screen** — it now opens like a normal app, full-screen, fully offline
4. Tap **+** to add your first entry

That's the whole setup. There is no step 5.

**Back up your data regularly** — tap **Export** to save a dated `.json` file to your Downloads folder. Browser storage can be cleared by the OS or by clearing site data, but an exported file is safe on your device independent of the browser.

## Tech stack

Plain HTML, CSS, and vanilla JavaScript. One file. No React, no npm, no bundler, no CDN calls, no analytics, no telemetry.

This is a deliberate constraint, not a limitation — see [Contributing](#contributing) below.

---

## Contributing

Contributions are welcome — the project is intentionally small, and that's meant to stay true.

### The one hard rule: don't grow it

Before opening a PR, ask: *does this feature genuinely need more code than it saves the user in effort?* A feature that adds 200 lines to save one tap usually isn't worth it here. This project optimizes for **staying inspectable in five minutes and loadable in under a second**, not for feature completeness.

Guidelines to keep contributions in that spirit:

- **Stay single-file.** No build step, no bundlers, no package.json. If your change needs a dependency, it probably doesn't belong here.
- **Prefer editing over adding.** If a new feature can reuse an existing UI pattern (the modal, the card list, the stat chips) instead of introducing a new one, reuse it.
- **No new libraries.** Everything should still run by double-clicking the file — that's non-negotiable.
- **Keep it readable.** Someone should be able to open the file, search for a function name, and understand what it does without cross-referencing five other files (because there are no other files).
- **Test on mobile.** This is built for Android home-screen use first — check that your change doesn't break narrow viewports.

### How to contribute

1. Fork the repo
2. Make your change in `loan-manager.html` directly
3. Test it by just opening the file in a browser (no build/setup needed — that's the point)
4. Open a PR describing **what** changed and **why it stays lightweight**
5. Small, focused PRs get reviewed faster than large ones — split unrelated changes into separate PRs

### Good first contributions

- Bug fixes in date handling, sorting, or the archive/unarchive logic
- Accessibility improvements (contrast, tap target sizing, screen reader labels)
- Small UX polish that doesn't add new screens
- Documentation improvements

### What's likely to be declined

- Cloud sync / accounts / login
- Multi-currency support (this is PKR-only by design)
- A build step, framework, or external dependency
- Anything that meaningfully increases file size for a niche use case

---

## Contribution status

🟢 **Open for contributions** — actively maintained, PRs and issues welcome.

| Area | Status |
|---|---|
| Core tracking (add/edit/delete) | Stable |
| Partial payments & auto-settle | Stable |
| People view + archive | Stable |
| Search & sort | Stable |
| Export/Import backup (cross-version) | Stable |
| Accessibility pass | Help wanted |
| Test coverage | Help wanted |
| Edit an existing entry in place | Help wanted |

## License

MIT — use it, fork it, ship it, no strings attached.

## About

Built as a lightweight, practical utility project — a deliberate exercise in solving a real personal problem (tracking informal PKR loans) with the smallest possible footprint, rather than reaching for a framework by default. Included here as a notable independent build: single-file architecture, no dependencies, and a full local-first data model (storage + backup/restore) designed and shipped end-to-end.
