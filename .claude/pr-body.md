# Retire prefix bridge + close/reopen workarounds; add step 5.7 (all 4 frameworks)

The Supabase→Vercel integration's per-connection prefix is configurable (field-verified Jun 2026;
supabase/supabase PR #28058 merged Jul 2024). Setting it to each framework's native prefix means
production and previews share the same env-var names — no cross-prefix fallback is needed.
Env sync also fires on push and branch creation, not only at PR-open (field-verified Jun 2026) —
so the "close and reopen the PR" workaround is also retired.

## What changed

- **New step 5.7** in all 4 `docs/<fw>/02-set-it-up.md` copies: sets the integration's
  per-connection prefix — Vite → `VITE_`, Astro → `PUBLIC_`, SvelteKit → `PUBLIC_`,
  Next.js → no change needed (default `NEXT_PUBLIC_` already matches).
- **Prefix bridge retired** in Vite, Astro, SvelteKit: removed the cross-prefix fallback
  chains (`VITE_ ?? NEXT_PUBLIC_`, `PUBLIC_ ?? NEXT_PUBLIC_`) from scaffold prompts, unit
  tests, architecture lines, self-checks, memory examples, audit prompts, and
  `06-keeping-it-current.md` env-name contract sections and workaround table rows.
- **Close/reopen workaround retired** in all 4 copies: step 6 ✗ and `/verify` skill
  updated to "push any commit to the PR branch — env sync fires on push and branch
  creation as well as PR-open"; workaround table row removed.
- **`docs/<fw>/07-decision-log.md`** (all 4 copies): env-var seam bullet corrected,
  verified-pass paragraph updated with field-verified Jun 2026 stamps for both retirements.
- **`docs/<fw>/01-the-model.md`** (all 4 copies): env-contract paragraph rewritten to
  name only the framework's native prefix and note step 5.7.
- **`MEMORY.md`**: per-framework env wiring section rewritten to document step 5.7, the
  native prefix per framework, and both retirements with canonical stamps.
- **Three earlier arrow-rule fixes** (constitution block) included from the prior scope.
- **`.claude/review/`**: three reviewer verdicts refreshed for this PR.

## Self-check

- [x] base = main; exactly one PR
- [x] ≤ 1 migration, UTC-timestamped latest; new tables have RLS; src/types matches
- [x] tests/lint/typecheck/e2e green; happy AND unhappy paths exercised
- [x] scripts still named exactly `lint`, `typecheck`, `test`, and `e2e`
- [x] key read via the two-prefix fallback chain; envPrefix consistent; nothing hardcoded; no secret in code
- [x] irreversible actions guarded + idempotent + flagged
- [x] no avoidable debt; memory updated and pruned
- [x] migrations explained in plain English
- [x] reviewers ran — `.claude/review/*` verdicts refreshed this PR
- [x] every subagent dispatched on a model below the orchestrator's — never inherited

## For you
**What changed:** Step 5.7 added to all 4 framework guides to set the Supabase→Vercel integration prefix to each framework's native name (`VITE_`, `PUBLIC_`, or unchanged for Next.js); the cross-prefix fallback chains and "close and reopen the PR" instruction are retired from all 4 copies; decision logs, env-contract paragraphs, workaround tables, and MEMORY.md updated throughout.
**What you do next:** Review the diff, then merge into `main`. In your own Supabase project, go to Settings → Integrations → Vercel → Manage and set Prefix to `VITE_` (since Dinh-Ngoc-Edu is a Vite app); after that, remove the `NEXT_PUBLIC_` fallback chain from `supabaseClient.ts` and `vite.config.ts` in a separate PR into that repo.
**How to roll it back:** Revert this PR; all 4 copies of `01`, `02`, `06`, `07`, plus `MEMORY.md`, return to their pre-PR state.
