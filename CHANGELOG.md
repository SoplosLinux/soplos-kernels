# Changelog — soplos-kernels

All notable changes to the Soplos kernel catalog (which variants and
hardware levels are compiled per kernel version). Built from the real
package inventory in `/home/soplos/Descargas/SoplosApps/kernels/` and the
external archive at `/run/media/soplos/Seagate Hub/Subdes/Soplos Apps/kernels/`
(6.18.52 LTS, 7.0.3 through 7.2.10), not from assumption — dates are
`.deb` file timestamps (preserved across the copy to external storage),
not commit history.

## Full catalog inventory by version

| Version | Date | Variants | March levels |
|---|---|---|---|
| 7.0.3 | 2026-06-01 | soplos, bore, bore-ntsync, ntsync, rt, zen | unmarked (v1 only — march selector not yet implemented) |
| 7.0.5 | 2026-06-01 | same 6 | unmarked |
| 7.0.9 | 2026-06-01 | same 6 | unmarked |
| 7.0.11 | 2026-06-01 | same 6 | unmarked |
| 7.0.12 | 2026-06-12 | same 6 | unmarked |
| 7.1.0 | 2026-06-15 | same 6 | unmarked |
| 7.1.1 | 2026-06-26 | same 6 | unmarked |
| 7.1.3 | 2026-07-16 | same 6 | unmarked |
| 7.1.4 | 2026-07-20 | soplos, bore, bore-ntsync, ntsync, rt, zen, x3d | published as V1-V4 (x3d: V3/V4 only), but binarily all V1 — march selector broken until 1.0.1-9 (2026-08-13), see entry below |
| 7.1.5 | 2026-07-25 | same 7 | published as V1-V4, binarily all V1 — same broken-selector window |
| 7.1.7 | 2026-08-07 | same 7 | published as V1-V4, binarily all V1 — same broken-selector window |
| 7.1.8 | 2026-08-14 | same 7 — last version with standalone bore and standalone ntsync | V1-V4 genuine — first version built after the 1.0.1-9 fix |
| 7.2.0 | 2026-08-18 | soplos, bore-ntsync, rt, zen, x3d | V1, V3 only |
| 7.2.2 | 2026-08-28 | same 5 | V1, V3 only |
| 7.2.3 | 2026-09-04 | same 5 | V1, V3 only |
| 7.2.4 | 2026-09-10 | same 5 (rebuilt as package revision `-2` after initial `-1`) | V1, V3 only |
| 7.2.5 | 2026-09-12 | soplos, bore-ntsync, rt, zen, x3d | V1-V4 (x3d: V3/V4 only) — full range restored |
| 6.18.52 | 2026-09-14 | lts (single variant) | V1-V4 |
| 7.2.6 | 2026-09-15 | soplos, bore-ntsync, rt, zen, x3d | V1-V4 (x3d: V3/V4 only) — `rt` rebuilt as revision `-2` on 2026-09-20/21 (all 4 march levels) |
| 7.2.7 | 2026-09-23/24 | soplos, bore-ntsync, rt, zen, x3d | V1-V4 (x3d: V3/V4 only) |
| 7.2.8 | 2026-09-26 | soplos, bore-ntsync, rt, zen, x3d | V1-V4 (x3d: V3/V4 only) |
| 7.2.9 | 2026-10-04 | soplos, bore-ntsync, rt, zen, x3d | V1-V4 (x3d: V3/V4 only) |
| 7.2.10 | 2026-10-12 | soplos, bore-ntsync, rt, zen, x3d | V1-V4 (x3d: V3/V4 only) |
| 7.2.11 | 2026-10-16 | soplos, bore-ntsync, rt, zen, x3d | V1-V4 (x3d: V3/V4 only) |
| 7.3 | 2026-10-19 | soplos, bore-ntsync, rt, zen, x3d | V1-V4 (x3d: V3/V4 only) |

---

## 7.3 — 2026-10-19

Full V1-V4 catalog build, same variant set as 7.2.5/7.2.9/7.2.10/7.2.11 (soplos,
bore-ntsync, rt, zen, x3d). Initial release of the 7.3 series.

- Updated base to Linux 7.3.
- Waydroid binder enabled across all variants.
- Real-time (`rt`) variant built with adapted 7.3 compatibility patch (`rt-i915-soplos`).
- Available across all microarchitecture levels V1–V4 (x3d: V3 and V4 only).

## 7.2.11 — 2026-10-16

Full V1-V4 catalog build, same variant set as 7.2.5/7.2.9/7.2.10 (soplos,
bore-ntsync, rt, zen, x3d).

### Fixed

- Zen build failed at V2 and above until `zen-soplos` 1.1.7
  (`0001-zen-7.2.patch`, generic) landed: the version-specific patch used
  for 7.2.9 didn't exist for 7.2.11, so the installer fell back to the
  stale generic patch, which failed its own dry-run and fell back again to
  zen-kernel's official upstream release — whose `CONFIG_X86_64_VERSION`
  march mechanism then conflicted with `soplos-cpu-kernel-patch`'s
  ISA-level patch past V1. Fixed at the source in `zen-soplos` 1.1.7
  instead of with another version-specific patch.

## 7.2.10 — 2026-10-12

Full V1-V4 catalog build, same variant set as 7.2.5/7.2.9 (soplos,
bore-ntsync, rt, zen, x3d). Zen compiled cleanly at every march level this
time only because `zen-soplos`'s fallback to zen-kernel's official upstream
release happened not to conflict with `soplos-cpu-kernel-patch`'s ISA-level
patch for this specific point release — see `zen-soplos` CHANGELOG 1.1.7:
the real, version-independent fix for this class of failure landed after
this build, once 7.2.11 hit the same conflict and this one didn't.

## 7.2.9 — 2026-10-04

Full V1-V4 catalog build, same variant set as 7.2.5 (soplos, bore-ntsync,
rt, zen, x3d). Required `zen-soplos` 1.1.6 (`0001-zen-7.2.9.patch`,
version-specific) to get Zen building at V2-V4 — the generic
`0001-zen-7.2.patch` available at the time still had stale Makefile/Kconfig
context from the original 7.2.0 base and fell back to zen-kernel's official
upstream release, which conflicted with the ISA-level patch past V1.

## 7.2.8 — 2026-09-26

Full V1-V4 catalog build, same variant set as 7.2.5/7.2.6/7.2.7 (soplos,
bore-ntsync, rt, zen, x3d). Single clean build, no revisions.

## 7.2.7 — 2026-09-23 / 2026-09-24

Full V1-V4 catalog build, same variant set as 7.2.5/7.2.6 (soplos,
bore-ntsync, rt, zen, x3d). V1 built 2026-09-23, V2-V4 the following day
(2026-09-24) — same build run spanning two calendar days, not a separate
revision.

## 7.2.6 — 2026-09-15

Full V1-V4 catalog build, same variant set as 7.2.5 (soplos, bore-ntsync,
rt, zen, x3d), built 2026-09-15.

### Fixed

- `rt` variant rebuilt as package revision `-2` on 2026-09-20 (V1) and
  2026-09-21 (V2-V4): the RT/i915 fix — mainline marks `DRM_I915` as
  `depends on !PREEMPT_RT`, so every RT kernel up to this point lost the
  Intel graphics driver silently at `olddefconfig`, see
  `soplos-kernel-installer` CHANGELOG 1.0.2-7 and the `rt-i915-soplos`
  patch. Only `rt` was rebuilt; the other 4 variants at all 4 march levels
  are unaffected and keep their original `-1` revision from 2026-09-15.

## 6.18.52 — 2026-09-14

### Added

- `linux-soplos-lts` — a separate LTS kernel line, single variant (no
  bore/rt/zen/x3d combinations), published at V1-V4. First and so far only
  entry in this catalog outside the 7.x line.

## 7.2.5 — 2026-09-12

### Added

- V2 and V4 march levels, reintroduced after being dropped for the 7.2–7.2.4
  range. This is not a regression fix — V2/V4 were deliberately dropped at
  7.2.0 (see below), then requested back by the community, and reintroduced
  here. Full V1-V4 range restored.

### Notes

- Binder/Waydroid support is not new here — it was already working as of
  7.2.4's revision `-2` (see below). 7.2.5 simply inherits that fix; it was
  not introduced in this version.

## 7.2.4 — 2026-09-10

### Fixed

- Package revision `-1` shipped with `CONFIG_ANDROID_BINDER_IPC` set as a
  module (`--module`, i.e. `=m`), an invalid value for what is actually a
  plain `bool` Kconfig symbol — silently normalized back to `n` by `make
  olddefconfig` (see `soplos-kernel-installer` 1.0.2-4/1.0.2-5). Binder was
  enabled in name only; Waydroid did not work on this build.
- Revision `-2` (in `rev1/`) rebuilt with `--enable` instead, the only valid
  form for this symbol — confirmed working with Waydroid. Rebuilt for 4
  variants at V1 (soplos, bore-ntsync, rt, zen) and 5 at V3 (the same 4 plus
  x3d, which is V3/V4-only and has no V1 build).

## 7.1.8 — 2026-08-14

### Fixed

- First kernel version built after `soplos-kernel-installer` 1.0.1-9
  (2026-08-13) fixed the march level selector. From 7.1.4 through 7.1.7
  (2026-07-20 – 2026-08-07), the selector wrote
  `CONFIG_GENERIC_CPU{2,3,4}` — symbols that don't exist in mainline —
  silently dropped by `olddefconfig`, so every kernel published as
  `-v2`/`-v3`/`-v4` in that window was binarily identical to `-v1` despite
  the label. Fixed by switching to `soplos-cpu-kernel-patch`'s real
  `X86_64_ISA_V1`–`V4` Kconfig choice. 7.1.8 is the first version in this
  catalog where the V1-V4 labels reflect genuinely different binaries.

## 7.2.0 — 2026-08-18

### Removed

- Standalone `linux-soplos-bore` and `linux-soplos-ntsync` packages,
  permanently. Deliberate catalog consolidation: both use cases are already
  covered by `linux-soplos-bore-ntsync`, making the standalone packages
  redundant. This is a design decision, not a gap to fill back in.
- V2 and V4 march levels. Deliberate catalog decision at the time — only V1
  and V3 were kept in the release lineup. (Reintroduced later at 7.2.5, see
  above.)

## 7.1.4 — 2026-07-20

### Added

- `linux-soplos-x3d` variant, available at V3/V4 only (X3D CPUs are Zen 3 or
  newer, matching the v3 microarchitecture floor).
- Per-level march builds (V1-V4) for every variant, replacing the previous
  unmarked (v1-only) builds.

## 7.0.3 — 2026-06-01

Initial tracked catalog.

### Added

- `linux-soplos`, `linux-soplos-bore`, `linux-soplos-bore-ntsync`,
  `linux-soplos-ntsync`, `linux-soplos-rt`, `linux-soplos-zen` — no march
  level selector yet, single unmarked build per variant.
