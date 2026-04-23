# Changelog

## v0.17.7 — 2026-04-23

### Added
- `/visual-plan` skill — **3rd and final meta-skill** in the
  `brainstorm → spec → plan → execute` architecture. Completes the triad:
  - `/visual-brainstorm` (v0.17.3/v0.17.4) produces `proposal.md`
  - `/visual-spec` (v0.17.5/v0.17.6) resolves into `design.md`
  - `/visual-plan` (this release) executes → `plan.md` + `iters/*.png` +
    `plan.md.results.jsonl` → terminal artifact `{completed, partial, aborted}`.
  See `skills/visual-plan/SKILL.md` (~413 lines). Mirrored byte-identical
  from vulca main repo `.claude/skills/visual-plan/SKILL.md` at v0.17.7.
- 4 phases (precondition+derivation → plan-review loop with 5-turn cap →
  execution loop → finalize + hygiene), 7 invariants S1-S7, 16-row error
  matrix with verbatim `Print exactly:` strings, 8-variant handoff set.

### Ship-gate status (upstream)
- Layer A pytest: 57/57 PASS <30s
- Layer B simulated (3 parallel subagents, 14 cases): **14/14 PASS**
- Layer C live v2 (2 parallel subagents, 6 gaps / 4 cases): **4/4 PASS**
- Combined: 18/18 for non-pixel-heavy surface.

### Dependencies
Requires v0.17.6 (also bundled into this PR) for `generate_image` MCP
extension (`seed/steps/cfg_scale/negative_prompt` kwargs) + `schema_version`
field in `design.md` frontmatter.

### Superseded (still active from v0.17.6 bundling)
This PR now supersedes open plugin PRs #3 (`sync/v0.17.4`
/visual-brainstorm) and #4 (`sync/v0.17.5` /visual-spec first ship).
Both remain superseded by this branch; close #3 and #4 after merging.

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

## v0.17.3 — 2026-04-21

### Added
- `/visual-brainstorm` skill — mirrored from vulca main repo. Guide fuzzy
  visual intent into proposal.md.
  See `skills/visual-brainstorm/SKILL.md`.
