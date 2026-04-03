# Scripts — CLAUDE.md
**Owner:** Brandon Markel
**Type:** Personal folder — Brandon-managed
**Last updated:** Apr 3, 2026

---

## What is this folder?

Terminal commands and scripting tools. Contains `timmy`, `stephen`, and `fart`. All art is embedded directly in the scripts — no external txt files needed. See `SESSION-NOTES.md` for full details on every file, how the commands work, and the GitHub repo.

**GitHub repo:** https://github.com/DrMarkel/terminal-scripts

## The Commands

- `timmy` — prints Timmy Burch ASCII art from South Park. Alternates between 2 arts (no repeats). Shows a larry3d block letter banner. Random yell line below.
- `stephen` — prints Stephen Hawking ASCII art. Cycles through 3 arts in order. Art 3 has "just chilling" banner embedded inside the image. Shows a random Hawking quote.
- `fart` — animated 11-frame frog fart story. Frogs use jgs-style wide flat design with eye expression changes per frame.

## Files in This Folder

| File | What it is |
|------|------------|
| `timmy` | Shell command — Timmy Burch art |
| `stephen` | Shell command — Stephen Hawking art |
| `fart` | Shell command — animated frog fart story |
| `.gitignore` | Excludes images, state files, plugin files, .DS_Store |
| `CLAUDE.md` | This file — instructions for Claude |
| `SESSION-LOG.md` | Log of every session and what changed |
| `SESSION-NOTES.md` | Full reference doc — how commands work, history |
| `install-commands.txt` | Shareable install instructions for Mac and Windows |
| `.stephen_state` | Tracks which Stephen art runs next (not in git) |
| `*.png` | Reference images (not in git) |

## Rules for Any Session

1. **Do not touch anything without Brandon's explicit request.** No cleanup, no reorganization, no "improvements" unless asked.
2. **Log what you did.** Before closing, append a dated entry to `SESSION-LOG.md`.
3. **Do not delete files.** If something seems unnecessary, tell Brandon — don't remove it.
4. **Keep scripts executable.** If you create a new script, run `chmod +x`.
5. **SESSION-NOTES.md is the reference doc.** If you add a new command or file, update it.

## Session Log Format

Append to `SESSION-LOG.md`:
```
## [Date] — [Session type]
**What I did:**
- [file]: [created/modified/deleted] — [one-line description]

**Files in folder after this session:** [count]
```
