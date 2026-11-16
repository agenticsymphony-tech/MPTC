# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Entries are derived from `git log` only. This repository's history is short: the whole
library arrived in two initial commits, and everything after v0.1.0 is documentation and
dotfiles. The changelog says so rather than manufacturing a feature narrative.

## [Unreleased]

### Added

- `CONTRIBUTING.md` — issue/PR/security paths and a list of good first issues (`a6818d9`).
- `SECURITY.md` — private-advisory reporting policy (`2524826`).
- `.github/PULL_REQUEST_TEMPLATE.md` (`f238364`).
- `.editorconfig` (`024929f`).
- `docs/banner.svg` and a CapsuleCraft-style README header (`662339a`, `ce315b0`).
- README links to contributing, discussions, security policy and good first issues (`5783d35`).

### Changed

- README formatting and badge block (`dd373ef`).

No source, header or example files were touched after v0.1.0
(`git diff --stat v0.1.0..HEAD` touches only `README.md`, `CONTRIBUTING.md`, `SECURITY.md`,
`.editorconfig`, `.github/PULL_REQUEST_TEMPLATE.md` and `docs/banner.svg`).

## [0.1.0] — 2026-07-31

Tag `v0.1.0` points at `1952303` (2026-07-31); the GitHub release was published 2026-10-16.

### Added

- **Library headers** (`include/mptc/`): `sintmath.h` (branchless superposition select,
  fast sin/tanh/GELU, dual numbers, Q15), `sdft.h` (sliding DFT, O(N) per tick, Q31),
  `triple_pll.h` (median-of-3 jitter filter), `integral_img.h` (summed-area table),
  `ternary.h` (balanced ternary packed 3 trits per 5 bits), `bitonic.h` (branchless
  sorting networks, N=4..64), tied together by `mptc.h`, `mptc_types.h` and the
  compile-time switches in `mptc_config.h` (`ece65f1`, `b68235c`).
- **Implementation files** for the stateful modules: `src/mptc.c`, `src/sdft.c`,
  `src/integral_img.c`; the rest are header-only.
- **Build**: canonical CMake build (`CMakeLists.txt`) plus a plain `Makefile` fallback
  (`make`, `make test`, `make bench`).
- **Tests**: `tests/test_basic.c` (84 assertions) wired into `ctest`.
- **Examples**: `examples/pc/pc_benchmark.c` and an ESP32 PlatformIO demo
  (`examples/esp32_demo/`).
- **Docs**: Doxygen config (`docs/Doxyfile`), README with module table, API overview,
  benchmarks and integration options.
- **CI**: GitHub Actions workflow building with CMake and running `ctest` on
  `main`/`master` (`bb06dc8`, `b1d8b35`; an intermediate workflow was added and removed
  again within the same day — `c89d385`).
- `.gitignore` (`c46bbc9`).

### Changed

- **License switched to Apache-2.0** from the license the project started with
  (`1952303`) — patent grant, attribution and royalty-friendly terms.
  The `README` license badge was left pointing at MIT at the time; see the fix in
  the current tree.

### History note

Two initial commits (`b68235c` "Initial upload", `ece65f1` "Initial commit") and one
LICENSE merge-resolution commit (`b26b3ce`) carry the entire library. There is no
per-module commit history to itemise, so the module list above is taken from the tree
at `v0.1.0`, not from commit messages.

[Unreleased]: https://github.com/kostyk348/MPTC/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/kostyk348/MPTC/releases/tag/v0.1.0
