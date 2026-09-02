# <PROJECT NAME> — <one-line tagline>

<1-3 sentence description: what this project is, what it does. If it's a
prototype/research project rather than a production app, say so plainly here
(see DOGGO's README for an example: "This is not a production app.").>

See `docs/PROJECT_SUMMARY.md` for the current state (objective, scope,
current state, recent decisions, known limitations, next action — the part
that changes often) and `docs/PROJECT_PROGRESS.md` for what's being worked
on right now. This README stays a short pointer, not a duplicate of either —
don't let real content drift into this file instead of those.

## How to run it

<Exact steps to run/use the project. No build step? Say so. Needs a server,
an API key, a specific Python/Node version? State it here precisely — this
is the one doc a new person (or a fresh AI chat) needs to get the thing
running without guessing.>

### Dev panel settings sync (one-time Vercel setup)

The dev panel's SAVE button writes to `data/processed/dev-panel-settings.json`
in this repo via `api/save-settings.js` (CLAUDE.md Section 12l); LOAD/RESET
read it back the same way. Until the two env vars below are set on the
Vercel project, SAVE reports "Save failed" — expected until this is set up:

1. **`GITHUB_TOKEN`** — a GitHub fine-grained personal access token, scoped
   to only this repo (`LeisHo/Buttsons`), with **Contents: Read and write**
   permission and nothing else. Create one at github.com → Settings →
   Developer settings → Personal access tokens → Fine-grained tokens.
2. **`DEV_PANEL_SAVE_SECRET`** — an anti-abuse shared token (not a real
   secret — it also lives in the page's own client-side source, same as any
   other value there). Set it to the value already embedded in `index.html`'s
   `DEV_PANEL_SAVE_SECRET` constant — or change both to a new value together
   if you'd rather generate your own.

Add both under the Vercel project → Settings → Environment Variables, then
redeploy. `GITHUB_REPO`, `GITHUB_BRANCH`, and `SETTINGS_FILE_PATH` are
optional overrides (see `api/save-settings.js`) — the defaults already match
this repo. Claude Code cannot enter these into Vercel's dashboard itself
(entering API keys/tokens on your behalf is outside what it's allowed to
do) — this step needs a human.

## Project structure

```
<PROJECT NAME>/
├── src/                     <what actually ships — see docs/CODE_SUMMARY.md>
├── data/
│   ├── raw/                 <scraped/dumped/regenerable inputs — gitignored>
│   └── processed/           <data the app actually reads>
├── docs/                    <README (pointer only — this file), PROJECT_SUMMARY.md,
│                             CODE_SUMMARY.md, HANDOFF.md, CHANGELOG.txt>
├── scripts/
│   ├── active/               <scripts still run regularly>
│   └── archive/               <one-off scripts that already did their job>
├── logs/                    <log entries from tests, audits, queries, etc>
├── results/                 <raw results of tests/runs>
└── tests/                   <if a real test suite exists>
```

<Adjust this tree to the project's actual layout — this is the standard
skeleton (CLAUDE.md §11), not every project needs every folder. A project
small enough to justify a single-file architecture can skip most of this
and say so explicitly in its own CLAUDE.md instead.>

## Known limitations

See `docs/PROJECT_SUMMARY.md`'s Known Limitations section for the current,
maintained list — not duplicated here to avoid drift between two copies of
the same information.

## Roadmap

No formal roadmap is tracked separately. See `docs/PROJECT_PROGRESS.md` for
what's currently being worked on and what's next, and `docs/CHANGELOG.txt`
for the full history of what's been built.
