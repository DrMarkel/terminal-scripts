# Session Notes — Timmy ASCII Art & Terminal Commands
**Date:** April 1, 2026
**Session type:** Cowork (Claude Desktop)

---

## What We Did

### 1. Attempted hand-drawn ASCII art of Timmy Burch (South Park)
- Made 10 versions using block characters (`▄▀█░▒▓`), box-drawing chars, and standard ASCII
- Results were generic — didn't actually look like Timmy
- Honest assessment: hand-drawing blind without pixel reference doesn't work for character-specific art

### 2. Switched to image-to-ASCII conversion (the right approach)
- Found the official South Park wiki PNG of Timmy (524×1029) already open in Arc browser
- Built a Python script (`img_to_ascii.py`) that converts any image to ASCII using half-block chars (`▀▄█`) or shade blocks (`░▒▓█`)
- Programmatically drew Timmy in PIL/Python (`draw_timmy.py`) based on the reference:
  - Giant round head (~60% of total height)
  - Orange spiky hair
  - Huge white oval eyes with tiny dot pupils
  - Worried/sad brows
  - Small downturned mouth
  - Tiny red shirt body
  - Dark brown wheelchair frame, blue backrest, teal footrest, gray side wheels
- Ran the drawing through the converter at multiple widths and modes
- Best result: 100-column half-block mode — clearly recognizable as Timmy

### 3. You uploaded 3 real Timmy ASCII arts
- **`timmy-art-1.txt`** — 108 lines, full wheelchair with large spoke wheels, open/airy style
- **`timmy-art-2.txt`** — 52 lines, dense `*` shading, more abstract
- **`timmy-art-3.txt`** — 70 lines, dense `@%#*+` shading, angled/complex view
- These are high quality and clearly recognizable

### 4. Built the `timmy` terminal command
- Shell script (`/Scripts/timmy`)
- Randomly picks one of the 3 uploaded arts each run
- Prints a large TIMMAAAY! ASCII banner (big block letters)
- Prints a random yell variant: `TIMMAY!`, `TIIIMMMAAAAYYY!`, `T I M M A A A A A Y ! ! !`, etc.
- ANSI colors: orange `@` for hair, brown `*#` for wheelchair, teal `=+` for footrest
- Auto-strips color when output is piped (CI logs stay clean)
- Exit code passthrough: `timmy 1` prints Timmy and exits 1 — useful as a build failure hook

### 5. Discovered the `fart` script already existed in Scripts
- Animated terminal story: 3 frogs progressively farting, escalating to total destruction
- 11 frames with `sleep` delays, full ASCII animation
- Was not in PATH — neither `fart` nor `timmy` were accessible as commands

### 6. Fixed PATH setup
- `~/.zshrc` had `~/bin` and `~/.local/bin` but NOT `Gay.Claude/Scripts`
- Fix: add this to `~/.zshrc`:
  ```bash
  export PATH="$HOME/Desktop/Gay.Claude/Scripts:$PATH"
  ```
  Then: `source ~/.zshrc`
- After this, both `fart` and `timmy` work from any terminal window

### 7. GitHub repo setup (in progress)
- Goal: push `fart` and `timmy` to a public repo so you can share with your brother
- Repo name: `DrMarkel/terminal-scripts`
- Install GitHub CLI if needed: `brew install gh && gh auth login`
- Then push:
  ```bash
  cd ~/Desktop/Gay.Claude/Scripts
  git init
  git add fart timmy
  git commit -m "initial commit: fart and timmy terminal commands"
  gh repo create DrMarkel/terminal-scripts --public --description "Custom terminal commands — fart, timmy, and whatever comes next" --source=. --push
  ```
- Your brother installs with:
  ```bash
  git clone https://github.com/DrMarkel/terminal-scripts ~/terminal-scripts
  echo 'export PATH="$HOME/terminal-scripts:$PATH"' >> ~/.zshrc && source ~/.zshrc
  ```

---

## Files in Gay.Claude/Scripts

| File | What it is |
|------|-----------|
| `timmy` | Shell command — run from anywhere, prints Timmy + TIMMAAAY banner |
| `fart` | Shell command — animated frog fart story, 11 frames |
| `timmy-art-1.txt` | Source ASCII art #1 (108 lines, spoke wheels) |
| `timmy-art-2.txt` | Source ASCII art #2 (52 lines, dense * shading) |
| `timmy-art-3.txt` | Source ASCII art #3 (70 lines, dense @%# shading) |
| `timmy-drawn.png` | Programmatically drawn Timmy reference image (PIL/Python) |
| `draw_timmy.py` | Python script that drew Timmy — edit to adjust proportions, re-run to regenerate |
| `img_to_ascii.py` | Image-to-ASCII converter — feed any PNG, get block art output |
| `timmy burch.png` | Original Timmy image (pre-existing) |
| `Timmy.webp` | Original Timmy image (pre-existing) |
| `stephen-hawking.avif` | Stephen Hawking image (pre-existing, presumably for a future command) |

---

## Key Takeaways / Lessons Learned

- **Hand-drawn ASCII art is basically guesswork** — image-to-ASCII conversion from a real reference is the only way to get character-accurate results
- **`img_to_ascii.py` is reusable** — drop any image in, get ASCII out. Good pipeline for making more commands (Stephen Hawking is right there...)
- **The PATH issue** — `Gay.Claude/Scripts` needs to be in `~/.zshrc` to make scripts available globally. One-time fix, then everything just works
- **Exit code passthrough** is a useful pattern — `timmy $?` at the end of a script prints Timmy only on failure

---

## For the Folder Manager

- `SESSION-NOTES.md` (this file) — keep in `Scripts/` as a running log
- The `timmy` command is production-ready, executable, and in PATH after the `~/.zshrc` fix
- GitHub repo push is pending — commands above will complete it
- `draw_timmy.py` and `img_to_ascii.py` are tools, not commands — they live in Scripts but don't need to be in the repo unless you want to version them too
