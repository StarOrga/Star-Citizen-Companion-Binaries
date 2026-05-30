# Star-Citizen-Companion-Binaries

**Public mirror of SC Companion desktop-tool binaries.**

This repository's sole purpose is to host the desktop-tool installer
binaries (`.exe` + `.blockmap`) for **end-user auto-update**. The actual
source code lives in the private repository
[Jerry0022/Star-Citizen-Companion-Website](https://github.com/Jerry0022/Star-Citizen-Companion-Website).

## Why a separate repo?

The source repository is private (alpha-phase WIP code). End-users with the
installed Tool need to download update binaries via `electron-updater`, which
has no GitHub authentication — so the binaries must live behind a publicly
fetchable URL.

The cleanest solution: a separate public repo just for releases. Source
remains private; binaries are public via GitHub Releases.

See [Star-Citizen-Companion-Website issue #7](https://github.com/Jerry0022/Star-Citizen-Companion-Website/issues/7)
for the full reasoning + alternatives considered.

## How it works

1. A tag `desktop-v*` pushed on the source repo triggers
   `.github/workflows/desktop-tool-build.yml`.
2. The workflow builds the Windows installer (NSIS + portable) on
   `windows-latest`.
3. After the build, it creates a Release **on this repo** using a fine-grained
   Personal Access Token stored as `BINARIES_RELEASE_TOKEN` in the source
   repo's Actions secrets. The PAT's resource owner must be the **StarOrga**
   organization, scope: `Contents: Read and write` on this repo only.
4. The release assets are public — `electron-updater` fetches them without
   any authentication.

## What you'll find here

- **No source code.** This repo will only ever contain this README + the
  per-release `.exe` / `.blockmap` files.
- **Releases tagged `desktop-v*`** mirroring the source repo's tags exactly.
- **No issue tracker.** Bugs go to the source repo:
  [Star-Citizen-Companion-Website/issues](https://github.com/Jerry0022/Star-Citizen-Companion-Website/issues).

## License

**Proprietary — All Rights Reserved.** The hosted binaries are NOT open
source. They are provided under the terms of the [LICENSE](LICENSE) in this
repository, which permits end users only to download and run the unmodified
binaries for personal, non-commercial use. Copying, redistribution,
modification, reverse engineering, and commercial use are prohibited.

The underlying source code is in the private repository
[Star-Citizen-Companion-Website](https://github.com/Jerry0022/Star-Citizen-Companion-Website).
