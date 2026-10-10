# repository-usd-core-wheels

OpenUSD Python wheels built for platforms the package index ships none for, published as release assets.

## What it is for

The published usd-core package has no wheel for some platforms and no source distribution to build one from. This repository holds only the recipe that builds the missing wheels from the upstream OpenUSD source, and a pixi environment names the resulting release asset by URL.

## Build and run

Dispatch the build workflow with an OpenUSD ref and a release tag. It builds inside the upstream manylinux image and uploads the repaired wheels to that release.

## Licence

MIT. See [LICENSE](LICENSE).
