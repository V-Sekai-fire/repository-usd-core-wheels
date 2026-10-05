# repository-usd-core-wheels

OpenUSD Python wheels for Linux on 64-bit ARM, where the package index ships none, published as release assets.

## What it is for

The published usd-core package has no wheel for Linux on 64-bit ARM and no source distribution to build one from. This repository holds only the recipe that builds that wheel from the upstream OpenUSD source. Consumers reference the wheel by its release-asset URL.

## Build and run

Dispatch the build workflow with an OpenUSD ref and a release tag. It builds inside the manylinux image and uploads the repaired wheels to that release.

## Licence

This repository states no licence of its own. The wheels it builds carry OpenUSD's licence.
