# Arrow-rule fix + close two open currency items (all 4 frameworks)

Three bullets in the app-`CLAUDE.md` constitution block violated the guide's own arrow rule (arrows connect only literal on-screen labels). They are rewritten as full sentences, byte-identical across all 4 framework copies. Two open items in `MEMORY.md` are closed with verified stamps.

## What changed

- **`docs/<fw>/02-set-it-up.md`** (all 4 copies): three `→`-chained bullets in the
  constitution block (Memory "Cycle", "Worked/failed"; Your place "Flow") rewritten
  as full sentences — byte-identical across vite/next/astro/sveltekit.
- **`MEMORY.md`**: closed two open currency items with canonical `*(field, …)*` and
  `*(docs + field, …)*` stamps: (1) integration injects both PUBLISHABLE_KEY and
  ANON_KEY (field-only; official docs list only ANON_KEY); (2) prefix IS configurable
  via Supabase Settings → Integrations (docs + field; sources: supabase/supabase
  PR #28058 + vercel.com/marketplace/supabase Jun 2026). The Vite bridge's
  "Retire when…" condition is now met — a follow-up PR will retire it.
- **`.claude/review/`**: three reviewer verdicts refreshed for this PR.

## Gate

- [x] Goal restated; only what the task needs was touched.
- [x] Every platform claim verified against current official docs and stamped; none left older than ~6 months unchecked.
- [x] Shared content moved across ALL framework copies; each changed pipe's dependents moved with it; anchors / steps / headings still parallel.
- [x] The three reviewers ran; `.claude/review/` verdicts refreshed this PR.
- [x] Memory updated at the narrowest tier and pruned.
- [x] One PR, with a plain-English "what changed / how to undo" for the human.

## For you
**What changed:** Three arrow-violating bullets in the pasted `CLAUDE.md` constitution block are rewritten as full sentences across all 4 framework copies; two long-open MEMORY.md items are closed with canonical verification stamps.
**What you do next:** Review the diff, then merge into `main` — no dashboard steps needed. Note: a follow-up PR is needed to retire the Vite `envPrefix` bridge now that the Supabase prefix-configurability "Retire when…" condition is confirmed met.
**How to roll it back:** Revert this PR; all four `02-set-it-up.md` files and `MEMORY.md` return to their pre-PR state.
