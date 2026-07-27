# Release process

Releases are fully automated by GitHub Actions — no manual steps beyond merging.

## How a release happens

1. Commits land on `main` using [Conventional Commits](https://www.conventionalcommits.org/):
   - `fix: ...` bumps the patch version
   - `feat: ...` bumps the minor version
2. On every push to `main`, the `Release Please` workflow runs CI (ansible-lint, CodeQL), then [release-please](https://github.com/googleapis/release-please) opens or updates a release PR that:
   - bumps `version.rb`, the `version:` in `provisioner.yml`, and the version stamp in `templates/Hosts.template.yml`
   - updates `CHANGELOG.md`
3. Merging the release PR creates the GitHub release and tag.
4. The `Build Provisioner Artifact` workflow then checks out the tag (submodules included), fetches the sha256-verified core driver pinned in `driver.version`, and uploads four assets to the release:
   - `startcloud_generic_provisioner-<version>.tar.gz` + `.sha256` — the immutable, registry-shaped archive the provisioner catalog records
   - `startcloud_generic_provisioner.tar.gz` + `.sha256` — a version-less copy at a stable URL

## Guarantees

- **Tag ↔ version lockstep**: the build fails if `provisioner.yml` does not match the version being released.
- **Immutable assets**: rebuilds via manual dispatch check out the release tag — never `main` HEAD — so republished assets are byte-identical and published checksums never change.

## Rebuilding an existing release's assets

Run the `Build Provisioner Artifact` workflow via manual dispatch with the release's `version` (for example `0.2.2`) and its `tag_name`.
