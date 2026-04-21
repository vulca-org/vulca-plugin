# Changelog

## v0.17.5 — 2026-04-21

### Added
- `/visual-spec` skill — mirrored from vulca main repo v0.17.5. Meta-skill #2
  in the brainstorm → spec → plan → execute architecture. Consumes
  `proposal.md` from `/visual-brainstorm` (status: ready); produces
  `design.md` (status: resolved) for `/visual-plan`. 6 phases, 7 dimensions,
  9-error matrix, 6 skill bans. Fenced YAML in design.md carries
  `{value, source, confidence}` metadata on D2/F numerics.
  See `skills/visual-spec/SKILL.md`.

## v0.17.4 — 2026-04-21

### Changed
- `/visual-brainstorm` skill — mirrored from vulca main repo v0.17.4. Three
  clarifications to the `proposal.md` contract surfaced by the 2026-04-21 live
  ship-gate v2: frontmatter fence strictness (7 fields, no YAML comments),
  resume-path rules (skip A2, bump `updated:`), and §Error matrix #1 refusal
  promoted to `Print exactly:` for downstream grep reliability.
  See `skills/visual-brainstorm/SKILL.md`.

## v0.17.3 — 2026-04-21

### Added
- `/visual-brainstorm` skill — mirrored from vulca main repo. Guide fuzzy
  visual intent into proposal.md.
  See `skills/visual-brainstorm/SKILL.md`.
