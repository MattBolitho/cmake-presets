# CMake Presets

This repository contains my personal "starter" `CMakePresets.json` for platforms that I have access to.
These presets are to be adjusted for consuming projects, depending on their individual build requirements.

They make a few assumptions:

- Relatively modern compiler versions are available, i.e., those that support specifying the C++23 standard
- The [`mold` linker](https://github.com/rui314/mold "mold linker repository") is available on Linux platforms

A few other notes:

- The philosophy of release configurations is to amenable to link time optimisation (LTO). This should yield compact yet well optimised binaries in general.
  - However, optimisations are avoided that may go beyond standards (no `-ffast-math`, `--icf=safe` rather than `--icf=all`, etc.).
- `*-release-static` presets are provided to create executables that are as self-contained as possible (depending on the platform). This can be desirable for portable applications without `libc` versioning constraints, or for deploying applications in distroless containers.
- Presets for oneAPI and AOCC are not included. These compilers are forked from clang, so little effort is required to add minimal versions of these if desired.
