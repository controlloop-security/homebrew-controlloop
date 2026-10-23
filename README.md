# homebrew-controlloop

The Homebrew tap for [ControlLoop](https://github.com/controlloop-security/controlloop),
a local-first security scanner and deterministic CI gate for AI agents.

```bash
brew install controlloop-security/controlloop/controlloop
controlloop --version
```

## What the formula installs

`Formula/controlloop.rb` is written by the ControlLoop release pipeline
(`release-scripts/homebrew_formula.py` in the main repository) for each
tagged release, never by hand. It installs the standalone binary that
release already published, checksummed and attested on its GitHub Release
page:

| Platform | Binary |
| --- | --- |
| macOS, Apple Silicon | `controlloop-macos-arm64` |
| Linux, x86_64 | `controlloop-linux-x86_64` |
| Linux, arm64 | `controlloop-linux-arm64` |

macOS on Intel has no binary yet; the formula says so and names the
alternative, `uv tool install controlloop` or `pipx install controlloop`.

Until the first release that carries a formula is tagged, this tap has no
formula and `brew install` reports that the formula does not exist.

The test workflow runs on every change to the formula, installs it on
macOS (Apple Silicon) and Linux, runs its test block, a real scan and
`brew audit`; until the formula exists it ends with a notice instead.

## Verifying

Every checksum in the formula comes from the release's own `SHA256SUMS`
file, and every binary carries a GitHub build-provenance attestation:

```bash
gh attestation verify "$(brew --prefix controlloop)/bin/controlloop" --repo controlloop-security/controlloop
```

See [Release verification](https://github.com/controlloop-security/controlloop/blob/main/docs/reference/release-verification.md).

## Support

Questions and problems go to the
[main repository's issues](https://github.com/controlloop-security/controlloop/issues).
Security reports follow its
[security policy](https://github.com/controlloop-security/controlloop/blob/main/SECURITY.md).

## License

Apache-2.0, the same as ControlLoop.
