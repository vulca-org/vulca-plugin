# VULCA Release

Automate VULCA version release across all distribution channels.

TRIGGER when: user says "release", "发版", "publish version", "bump version", "push to PyPI", "sync repos", "update version to", or mentions releasing a new version number.

## MANDATORY: Use release.sh

**NEVER manually edit version numbers or push subtrees individually.** The ONLY correct way to release is:

```bash
./scripts/release.sh <version>
```

This script handles ALL 7 steps atomically:
1. Version bump in 5 files (vulca/pyproject.toml, _version.py, test, comfyui-vulca/pyproject.toml × 2)
2. Consistency verification
3. Git commit + tag
4. Subtree push to vulca-org/vulca (master)
5. Subtree push to vulca-org/vulca-plugin (main)
6. Subtree push to vulca-org/comfyui-vulca (main)
7. PyPI upload + GitHub release creation

## Instructions

When the user wants to release a new version:

1. **Confirm version number** — ask "What version? (current: check vulca/_version.py)"
2. **Pre-flight checks**:
   - All tests passing: `cd vulca && .venv/bin/python -m pytest tests/ -q --tb=no`
   - No uncommitted changes: `git status`
   - Confirm with user: "Ready to release v{X.Y.Z}? This will push to GitHub + PyPI."
3. **Run the script**:
   ```bash
   ./scripts/release.sh X.Y.Z
   ```
4. **Verify**:
   - `gh release list -R vulca-org/vulca --limit 1` → should show new version as Latest
   - `pip index versions vulca` → should show new version
5. **Report** the release URLs to user

## Why This Exists

Previous manual releases caused version drift across 5 distribution channels (monorepo, 3 GitHub repos, PyPI). v0.9.1 had: GitHub 235 commits behind, v0.3.0 marked as Latest, comfyui-vulca version mismatch. This script eliminates all manual steps.

## Anti-Patterns (NEVER DO)

- Manually editing `_version.py` without running release.sh
- Running `git subtree push` individually
- Creating GitHub releases via `gh release create` without the script
- Running `twine upload` separately
- Changing version in one file but not others
