---
description: Export a rendered deck to PDF with the global deck skill
argument-hint: <session number or filename>
allowed-tools: Bash(bash ~/.claude/skills/deck/assets/deck-to-pdf.sh:*)
---

Export the deck `$1` by running, from the project root:

```
bash ~/.claude/skills/deck/assets/deck-to-pdf.sh $1 --root docs --out pdf --size 1680x1120
```

Those three flags are all this repo contributes. Everything else — loose name
matching, re-rendering a stale deck, serving the site over HTTP, mirroring the
result — lives in the global `deck` skill at `~/.claude/skills/deck/`, so it
stays the same across every repo. Do not reimplement any of it here, and if the
export itself needs fixing, fix it there.

`--root docs` is the rendered site and `--out pdf` is the tracked copy; the
script mirrors each PDF into `docs/pdf/` so it is live on the served site
without a full re-render. `pdf/session01.pdf` through `session08.pdf` are in the
`resources:` list in `_quarto.yml`, so a later `quarto render` keeps that copy
rather than dropping it. Commit both.

`--size 1680x1120` overrides the skill's 1920x1200 default, and the override is
the reason this file exists. That default is 16:10 — deliberately taller than a
1920x1080 deck, to give back the margin decktape drops. These decks are shoji,
which is a 1050x700 (3:2) canvas with `margin: 0`, so there is no margin to give
back and a 16:10 viewport would just letterbox the slides with bands of page
either side. 1680x1120 is 1.6x the canvas, exactly 3:2, and lands a 1260x840pt
page. If a deck is ever built here on a different canvas, match its aspect ratio
rather than keeping this number.

Name the deck in full: `/deck session01`. The skill's loose matching splits a
stem on `_` (it is built for names like `3_teaching`), and `sessionNN` has no
underscore, so `/deck 01` and `/deck 1` match nothing here. Omit `$1` to export
every deck that is currently rendered under `docs/slides/`. If the name matches nothing the script lists what it found;
relay that list. Report where the PDF landed and its page count.

Only decks listed in the `render:` block of `_quarto.yml` reach `docs/slides/`
in the first place — that list is uncommented one session at a time as each deck
is finished, so an unfinished deck cannot be exported or published by accident.
