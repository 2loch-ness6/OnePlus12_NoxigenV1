# OnePlus 12 Noxigen V1 - Kernel Source Manifest

This repository contains the Android repo manifest for building the OnePlus 12 kernel with Noxigen modifications.

## Prerequisites

- Git
- Repo tool
- Linux build environment with at least 100GB of free disk space

## Installing Repo Tool

```bash
mkdir -p ~/bin
curl https://raw.githubusercontent.com/GerritCodeReview/git-repo/main/repo > ~/bin/repo
chmod a+x ~/bin/repo
export PATH=~/bin:$PATH
```

## Downloading the Source

Initialize the repository:

```bash
repo init --repo-url=https://github.com/GerritCodeReview/git-repo.git --no-repo-verify -u https://github.com/2loch-ness6/OnePlus12_NoxigenV1.git -b main -m oneplus_12_u.xml
```

Sync all projects:

```bash
repo sync -c -j$(nproc --all)
```

## What Gets Downloaded

This manifest will download:

- **Kernel Sources** from OnePlusOSS:
  - Common kernel platform
  - MSM kernel
  - Kernel modules and device tree

- **Build Tools** from CodeLinaro:
  - Prebuilt toolchains (Clang, GCC)
  - Bazel build system
  - JDK 11
  - Build utilities

## Manifest Structure

The manifest (`oneplus_12_u.xml`) defines 17 projects from two remote sources:
- **OnePlusOSS** (GitHub): OnePlus-specific kernel code
- **CodeLinaro** (clo-la): QCOM kernel platform and build tools

## Build Instructions

After syncing, refer to the kernel build documentation in the kernel_platform directories for build instructions specific to the OnePlus 12 (sm8650) platform.

## Notes

- This uses the oneplus/sm8650_u_14.0.0_oneplus12 branch for OnePlus sources
- CodeLinaro sources use specific commit SHAs for reproducible builds
- The `-c` flag in repo sync downloads only the current branch to save space
