# Session Notes — Timmy & Fart Terminal Commands
**Date:** April 1, 2026
**Session type:** Cowork (Claude Desktop)
**GitHub repo:** https://github.com/DrMarkel/terminal-scripts

---

## What Lives Where

### Primary folder: `~/Desktop/Gay.Claude/Scripts/`

| File | What it is | In GitHub? |
|------|------------|------------|
| `timmy` | Shell command — prints random Timmy ASCII art + TIMMAAAY! banner | ✅ Yes |
| `fart` | Shell command — animated 11-frame frog fart story | ✅ Yes |
| `timmy-art-1.txt` | Source ASCII art #1 (108 lines, spoke wheels, open style) | No |
| `timmy-art-2.txt` | Source ASCII art #2 (52 lines, dense `*` shading) | No |
| `timmy-art-3.txt` | Source ASCII art #3 (70 lines, dense `@%#` shading) | No |
| `timmy-drawn.png` | Programmatically drawn Timmy reference image | No |
| `draw_timmy.py` | Python script that drew Timmy using PIL | No |
| `img_to_ascii.py` | Image-to-ASCII converter — feed any PNG, get block art | No |
| `timmy burch.png` | Original Timmy reference image | No |
| `Timmy.webp` | Original Timmy reference image | No |
| `stephen-hawking.avif` | Stephen Hawking image (for a future command someday) | No |
| `SESSION-NOTES.md` | This file | No |

---

## The Commands

### `timmy`
Run it from anywhere in terminal: just type `timmy`

What it does:
- Randomly picks one of 3 uploaded Timmy ASCII arts each time you run it
- Prints a large **TIMMAAAY!** banner in block letters
- Prints a random yell variant: `TIMMAY!`, `TIIIMMMAAAAYYY!`, `T I M M A A A A A Y ! ! !`, etc.
- ANSI colors: orange for hair, brown for wheelchair, teal for footrest
- Auto-strips color when output is piped (so logs stay clean)
- **Exit code passthrough:** `timmy 1` prints Timmy and exits with code 1 — use it as a build failure hook: `some-command || timmy $?`

### `fart`
Run it from anywhere in terminal: just type `fart`

What it does:
- Animated 11-frame story in the terminal
- Three realistic frogs. One farts. Then another. Then the third one walks in and gets hit by a catastrophic combined blast.
- Eye expressions change per frame: `o o` normal → `O O` straining → `^ ^` smug → `> <` oh no → `x x` dead
- Final frame: all three frogs with `x x` eyes going `...ribbit...`
- Sound escalation: `p f f f f F F F R R R T T !` → `B B R R A A A P P ! ! !` → `F F F W W O O O M M P P P ! ! ! !`

---

## How They Got Built

### Timmy
1. Tried 10 hand-drawn ASCII attempts — all looked generic, not like Timmy
2. Switched to image-to-ASCII conversion pipeline:
   - Built `draw_timmy.py` to programmatically draw Timmy in Python/PIL (giant round head, orange hair, huge eyes, wheelchair)
   - Built `img_to_ascii.py` to convert any PNG to block characters (`▀▄█░▒▓`)
   - Best result: 100-column half-block mode — clearly recognizable
3. You then uploaded 3 real Timmy ASCII arts from the internet — these are what the command actually uses
4. Wrapped everything in a shell script with ANSI colors and random selection

### Fart
- Script already existed when this session started
- Rewrote it with realistic frog ASCII art (proper frog shape with body, legs, feet)
- Added per-frame eye expressions including `x x` dead eyes on the final frame
- Fixed centering across all 11 frames
- All three frogs die at the end

---

## PATH Setup (one-time fix)
Scripts only work as commands if this line is in `~/.zshrc`:

```bash
export PATH="$HOME/Desktop/Gay.Claude/Scripts:$PATH"
```

To add it (if not already there):
```bash
echo 'export PATH="$HOME/Desktop/Gay.Claude/Scripts:$PATH"' >> ~/.zshrc && source ~/.zshrc
```

---

## GitHub Repo
**URL:** https://github.com/DrMarkel/terminal-scripts

Contains: `fart` and `timmy`

To push future changes:
```bash
cd ~/Desktop/Gay.Claude/Scripts
git add <filename>
git commit -m "describe what changed"
git push
```

No Homebrew needed. `git` is built into macOS.

To share with your brother:
```bash
git clone https://github.com/DrMarkel/terminal-scripts ~/terminal-scripts
echo 'export PATH="$HOME/terminal-scripts:$PATH"' >> ~/.zshrc && source ~/.zshrc
```

---

## Tools Available for Future Commands

- **`img_to_ascii.py`** — drop any image in, get ASCII art out. Stephen Hawking is right there waiting.
- **`draw_timmy.py`** — tweak proportions or colors, re-run, regenerate the reference PNG
- The whole pipeline is reusable for any character or image

---

## Pending / Future Ideas
- [ ] Push updated `fart` to GitHub (realistic frogs + x eyes)
- [ ] Uninstall Homebrew (no longer needed — `gh` was the only thing using it)
- [ ] TMNT version of fart (noted, circling back later)
- [ ] Stephen Hawking command using `img_to_ascii.py`
