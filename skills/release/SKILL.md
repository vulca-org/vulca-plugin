# VULCA Release

Automate VULCA version release across all distribution channels.

TRIGGER when: user says "release", "发版", "publish version", "bump version", "push to PyPI", "sync repos", "update version to", or mentions releasing a new version number.

## MANDATORY: Use release.sh

**NEVER manually edit version numbers, push subtrees, or create releases individually.** The ONLY correct way to release is:

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

5. **Post-release verify ALL 4 repos + PyPI**:
   ```bash
   # GitHub releases (must ALL show v.X.Y.Z Latest)
   for repo in vulca-org/vulca vulca-org/vulca-plugin vulca-org/comfyui-vulca yha9806/vulca-platform; do
     echo "$repo: $(gh release list -R $repo --limit 1 --json tagName --jq '.[0].tagName')"
   done

   # PyPI
   pip index versions vulca | head -1

   # README version consistency
   grep -c "X.Y.Z" vulca/README.md vulca-plugin/README.md comfyui-vulca/README.md README.md
   ```

6. **Report ALL release URLs**:
   - SDK: https://github.com/vulca-org/vulca/releases/tag/vX.Y.Z
   - Plugin: https://github.com/vulca-org/vulca-plugin/releases/tag/vX.Y.Z
   - ComfyUI: https://github.com/vulca-org/comfyui-vulca/releases/tag/vX.Y.Z
   - Monorepo: https://github.com/yha9806/vulca-platform/releases/tag/vX.Y.Z
   - PyPI: https://pypi.org/project/vulca/X.Y.Z/

## What release.sh Does (12 steps)

1. Version bump in 5 code files
2. Version update in 4 READMEs
3. Test count auto-update in READMEs
4. Consistency verification
5. Git commit + tag
6. Push monorepo to origin (yha9806/vulca-platform)
7. Subtree push vulca-org/vulca
8. Subtree push vulca-org/vulca-plugin
9. Subtree push vulca-org/comfyui-vulca
10. PyPI build + upload
11. GitHub releases on ALL 4 repos
12. Summary report

## Anti-Patterns (NEVER DO)

- Manually editing _version.py without running release.sh
- Running git subtree push individually
- Creating GitHub releases via gh release create without the script
- Running twine upload separately
- Changing version in one file but not others
- Skipping dry-run on first use
- Forgetting to push monorepo (yha9806/vulca-platform)
- Creating release on some repos but not all 4
