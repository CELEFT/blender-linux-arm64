# CI for Blender (Linux Arm64)

A build system for automating the building of Blender for Linux Arm64, supporting GitHub Actions.

## Patches

In order to successfully build Blender on the Linux Arm64 platform, this project has added additional patches for some versions, which you can find in [this directory](https://github.com/lfdevs/blender-linux-arm64/tree/ci/patches). Some of these patches fix build errors of specific dependencies on the Linux Arm64 platform, while others remove components that are currently unavailable on the Linux Arm64 platform.

## Build
### GitHub Actions

This project supports building using [GitHub Actions](https://github.com/lfdevs/blender-linux-arm64/actions). You can fork this repository and then enable Actions in your fork.

[The workflow](https://github.com/lfdevs/blender-linux-arm64/blob/ci/.github/workflows/build.yml) have five input parameters when manually triggered, briefly introduced as follows:

1. Blender version tag

    Build target, only supports [tags in this page](https://github.com/lfdevs/blender-linux-arm64/tags). Tags for other versions are likely to fail the build due to the lack of patches.


2. Build type

    Build type, currently supports `release`, `lite`, and `debug`, refer to the official documentation: https://developer.blender.org/docs/handbook/building_blender/options/

3. GCC version

    The version of the GCC toolchain used when building dependencies and Blender, currently supports `14` and `11`. Versions `v5.1.0` and above require version `14`, see the upstream PR: [#149852 - Deps: Library changes for Blender 5.1 - blender - Blender Projects](https://projects.blender.org/blender/blender/pulls/149852)

4. Force rebuild dependencies

    Force rebuild dependencies instead of using dependencies successfully built for that tag previously (saved via GitHub Actions Caches, which expire after a certain period).

5. Draft a new release

    Automatically generate a draft release.

## Contributing

Submitting [PRs](https://github.com/lfdevs/blender-linux-arm64/pulls) is welcome—whether fixing bugs, adapting to various versions, or other improvements, all of which are highly beneficial to this project.

Discussions in [Issues](https://github.com/lfdevs/blender-linux-arm64/issues) are also welcome—whether reporting how the build artifacts perform on your device, or sharing adaptation or build experiences, all of which are very helpful to this project.

## Credits

- [Blender](https://www.blender.org/): The Free and Open Source 3D Creation Software.
