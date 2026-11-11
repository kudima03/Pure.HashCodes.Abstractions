# Changelog

All notable changes to Pure.HashCodes.Abstractions are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [1.0.0] — 2026-11-11

First stable release.

### Added

- Package now targets `net11.0`, in addition to `netstandard2.0`, `net7.0`,
  `net8.0`, `net9.0`, and `net10.0`.
- README is now packed into the NuGet package.

### Changed

- Assembly versions are now derived from the release tag.
- Package publishing uses NuGet trusted publishing.
- Package validation enabled to track public API compatibility; the public
  API is unchanged since 0.2.0.

## [0.2.0] — 2025-12-05

### Changed

- Package now multi-targets `netstandard2.0`, `net7.0`, `net8.0`, `net9.0`,
  and `net10.0`, in addition to the previous `net9.0`-only target.

## [0.1.0] — 2025-11-01

### Added

- **`IDeterminedHash`** — marker interface extending `IEnumerable<byte>`
  for representing a deterministic hash as a sequence of bytes.
