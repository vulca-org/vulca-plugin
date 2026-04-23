# Changelog

## v0.17.6 — 2026-04-23

### Added
- `/visual-spec` skill — meta-skill #2 of the `brainstorm → spec → plan`
  architecture. Turns a resolved `proposal.md` (from `/visual-brainstorm`) into
  a `design.md` with 7 technical dimensions (A: provider + params, B: composition
  strategy, C: prompt composition, D1: L1-L5 weights, D2: thresholds + batch,
  E: optional spike plan, F: cost budget). 6 phases (precondition gate → F
  calibration → dimension derivation → derive-then-review loop with 5-turn cap →
  optional spike → finalize), 9-error matrix, 6 skill bans (S1-S6), 5-word
  finalize vocabulary. See `skills/visual-spec/SKILL.md` (~440 lines).
  Mirrored byte-identical from vulca main repo `.claude/skills/visual-spec/SKILL.md`
  at v0.17.6.

### Changed
- `/visual-brainstorm` skill updated to vulca main v0.17.4:
  - Frontmatter schema tightened — "exactly 7 fields, no additional keys, no
    YAML comments inside the `---` fence".
  - §Opening turn 2 resume path (`status: draft`) — explicit rules: skip the A2
    solicited-sketch question; bump `updated:` to today on re-finalize;
    `created:` unchanged.
  - §Error matrix #1 — refusal phrase promoted to `Print exactly:` per §Handoff
    convention so downstream tooling can reliably grep for it.

- `/visual-spec` v0.17.5 → v0.17.6 clarity patches (10 items) folded in the
  same commit (no separate mirror needed since v0.17.5 never reached plugin main):
  - Err #9 Notes template wording normalized (`unreachable` → `unreadable`).
  - Err #5 / #6 classifier tightened with content-semantic keyword regexes
    (integration-layer vs per-call failure distinction); pipes unescaped and
    kept outside the Markdown table for correct Python / JS / PCRE parsing.
  - Multiplier table gains bare-`sdxl` row with host-detect resolution (darwin
    → `sdxl-mps`, else `sdxl-cuda`).
  - Phase 3.A: `recommended_providers` phantom key replaced with real
    `pipeline_variant` reference.
  - Phase 3.C: `tradition_tokens` real shape documented (`list[dict]` from
    `.terminology`, not flat bilingual strings) + concat recipe supplied.
  - Phase 3.D1: example weights annotated as illustrative; mechanical byte-copy
    rule re-emphasized.
  - Phase 2 Err #3 resume behavior specified: trust the draft's `F` block,
    do NOT re-calibrate mock latency.
  - Phase 4 `accept all` branch documents the finalize-`Write`-absorbs-bump
    exception to step 4's `Write`-pairs-with-every-`turns_used`-change rule.
  - §Produced artifact documents all 3 section-count cases (9 / 8 / 7) including
    the collapsed `tradition: null` + no-spike shape.
  - New `schema_version: "0.1"` frontmatter field (9 canonical fields total;
    additive — legacy drafts default to `"0.1"` on finalize with no retro-write).

### Superseded
- This PR supersedes open PRs #3 (`sync/v0.17.4` for /visual-brainstorm) and
  #4 (`sync/v0.17.5` for /visual-spec first ship). Both are bundled into this
  catch-up release. Close #3 and #4 after merging this PR.

## v0.17.3 — 2026-04-21

### Added
- `/visual-brainstorm` skill — mirrored from vulca main repo. Guide fuzzy
  visual intent into proposal.md.
  See `skills/visual-brainstorm/SKILL.md`.
