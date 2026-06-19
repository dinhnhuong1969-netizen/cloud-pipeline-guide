# currency-researcher — memory

Findings worth keeping between runs, one per line; prune to keep it short. The
orchestrator updates this file (the agent returns text and never commits).

- Framework env-wiring deltas were written from established `@supabase/ssr`
  patterns and still need a first official-docs pass: Next.js (`NEXT_PUBLIC_`,
  native — no fallback), Astro (`PUBLIC_` + `NEXT_PUBLIC_` via `astro.config.mjs`
  `vite.envPrefix`), SvelteKit (`PUBLIC_`, server resolves the fallback and passes
  values to the client). Verify each against current Supabase/Vercel/framework docs
  and stamp.
