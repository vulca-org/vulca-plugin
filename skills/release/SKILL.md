# VULCA Release

Automate VULCA version release across all distribution channels.

TRIGGER when: user says "release", "发版", "publish version", "bump version", "push to PyPI", "sync repos", "update version to", or mentions releasing a new version number.

## MANDATORY: Use release.sh

**NEVER manually edit version numbers or push subtrees individually.** The ONLY correct way to release is:

```bash
./scripts/release.sh <version>
```

## Instructions

When the user wants to release a new version:

1. **Confirm version number**:
   ```bash
   grep '__version__' vulca/src/vulca/_version.py
   ```
   Ask: "Current version is X.Y.Z. What's the new version?"

2. **Pre-flight checks**:
   ```bash
   cd vulca && .venv/bin/python -m pytest tests/ -q --tb=no
   git status
   ```
   All tests must pass. No uncommitted changes.

3. **Dry-run first**:
   ```bash
   ./scripts/release.sh --dry-run X.Y.Z
   ```
   Review the output with the user. Confirm before proceeding.

4. **Execute release**:
   ```bash
   ./scripts/release.sh X.Y.Z
   ```

5. **Post-release verify**:
   ```bash
   gh release list -R vulca-org/vulca --limit 1
   pip index versions vulca | head -1
   grep -c "X.Y.Z" vulca/README.md vulca-plugin/README.md comfyui-vulca/README.md README.md
   ```
   All 4 READMEs should reference the new version. GitHub release should show as Latest.

6. **Report** release URLs to user:
   - GitHub: https://github.com/vulca-org/vulca/releases/tag/vX.Y.Z
   - PyPI: https://pypi.org/project/vulca/X.Y.Z/

## What release.sh Does

1. Version bump in 5 files + README test count auto-update
2. Consistency verification
3. Git commit + tag
4. Subtree push to 3 GitHub repos (vulca, vulca-plugin, comfyui-vulca)
5. PyPI build + upload
6. GitHub release creation (Latest)

## Anti-Patterns (NEVER DO)

- Manually editing _version.py without running release.sh
- Running git subtree push individually
- Creating GitHub releases via gh release create without the script
- Running twine upload separately
- Changing version in one file but not others
- Skipping dry-run on first use
