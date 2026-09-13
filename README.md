# repository-usd-core-wheels

OpenUSD Python wheels for platforms upstream doesn't publish to pypi. Source
of truth is [PixarAnimationStudios/OpenUSD](https://github.com/PixarAnimationStudios/OpenUSD);
this repo holds only the build recipe and Release assets.

## What upstream publishes

usd-core on pypi ships wheels for `manylinux_2_28_x86_64`, `macosx_10_15_universal2`,
and `win_amd64`. The `universal2` mac wheel covers both arm64 and x86_64 macs;
the linux one is x86_64 only. No `manylinux_2_28_aarch64` wheel exists on pypi.

## What this repo publishes

Currently `manylinux_2_28_aarch64` for cp312/cp313/cp314, matching upstream's
python matrix on x86_64 and macOS. Wheels land as assets on GitHub Releases,
one release per upstream USD tag (e.g. `26.8-arm64-linux`).

## Building

Trigger `.github/workflows/build.yml` via `workflow_dispatch` with the OpenUSD
ref (branch/tag/SHA) and a release tag. The job runs on `ubuntu-24.04-arm`,
inside upstream's manylinux docker image with cmake, and mirrors upstream's
`build_scripts/pypi/` recipe. Repaired wheels upload to the named release.

## Consuming from pixi

```toml
[pypi-dependencies]
usd-core = { url = "https://github.com/V-Sekai-fire/repository-usd-core-wheels/releases/download/26.8-arm64-linux/usd_core-26.8-cp314-cp314-manylinux_2_28_aarch64.whl" }
```

Or add both x86_64 (pypi) and aarch64 (this repo) sources per-platform.

## Why not build from pypi source dist

usd-core doesn't publish an sdist — the pypi project is wheel-only. Building
requires the full OpenUSD source tree, hence the upstream checkout in the
workflow.
