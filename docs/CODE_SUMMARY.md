# Code Structure Summary

Status: see [../README.md](../README.md) for the project-structure layout and
how to run it; this file is a quick orientation pointer into the actual code,
not a duplicate of the README's tree.

---

## File Map

<One entry per real top-level module/folder -- what it contains and what it's
responsible for. Enough for a new session to know where to look for a given
concern without reading the whole codebase (per CLAUDE.md §0b's file-reading
efficiency guidance). Flag anything unused/leftover/dead explicitly rather
than silently listing it as if it were live -- e.g. "kept for reference, not
actively run.">

- `<path>` — <what it does, what it's responsible for.>

---

## Architecture

<The real shape of how the pieces fit together -- data flow, pipeline stages,
what depends on what and, just as importantly, what deliberately does NOT
depend on what (e.g. "analysis only ever reads the table ingestion already
wrote, never the other way around"). This is the section that saves a later
session from re-deriving the architecture by reading every file.>

---

## Untouchable Systems

<Subsystems that must not be touched incidentally -- live pipelines,
classification logic, tracking state, indexes, anything a casual edit could
silently break. State "None formally designated yet" if genuinely true for
an early-stage project, rather than leaving the section looking incomplete.>

---

## Gotchas

<Real bugs already hit and fixed, pinned-dependency reasons, ordering
requirements, non-obvious constraints -- anything a later session would
otherwise rediscover the hard way. One bullet per gotcha, concrete enough to
actually prevent the mistake:>

- <Gotcha> — <why it matters, what breaks if ignored.>
