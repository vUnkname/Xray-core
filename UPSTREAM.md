# Upstream sync (patterniha)

[vUnkname/Xray-core](https://github.com/vUnkname/Xray-core) is a fork of [patterniha/Xray-core](https://github.com/patterniha/Xray-core).

## Policy

- **Only** `patterniha/main` is merged into this repo’s `main`.
- vUnkname-specific changes (Android release matrix, asset naming, release upload tweaks) stay in this fork.
- [vXGram](https://github.com/vUnkname/vXGram) consumes **Release tags** from this repo (`XRAY_VERSION`); it does not merge Xray source.

## Automatic sync

Workflow [Sync patterniha main](.github/workflows/sync-patterniha.yml) runs daily and on manual dispatch:

1. Fetch `patterniha/main`
2. Merge into `main`
3. Push to `origin/main`

If the merge conflicts, the workflow fails; resolve conflicts locally and push, or fix in a PR.

## Manual sync

```bash
git fetch upstream   # remote: https://github.com/patterniha/Xray-core.git
git checkout main
git merge upstream/main
git push origin main
```

After a successful sync, run the **Release** workflow (or tag) to publish new Android ZIPs for vXGram.
