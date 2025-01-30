![SkylineUI](https://github.com/SkylineUI-reborn-dump/platform_manifest/blob/fifteen/SkylineUIBanner.png)

# Manifest SkylineUI #

### Install Git LFS ###

It is necessary to install Git LFS to avoid problems with gapps and repositories that are uploaded with Git LFS.

*Avoid this step if you already have Git LFS installed*.

Requirements
------------
- At least 250-300 GB free disk space.
- A computer/server with at least 16GB RAM running Linux and a fast & stable internet connection.
- Some basic knowledge of Linux commands, device tree management and git.

Instructions
------------
### Prerequisites
A properly configured build environment is required to build AOSP custom roms. A comprehensive guide for setting up the build environment can be found [here](https://source.android.com/setup/build/initializing).

Sync up the source
------------
```bash
sudo apt install git-lfs
git lfs install
```

### Sync SkylineUI Source ###

```bash
# Initialize local repository

mkdir SkylineUI
cd SkylineUI
```

- Repo Init Source
```bash
repo init -u https://github.com/SkylineUI-Reborn/platform_manifest.git -b fifteen --git-lfs
```
Now we proceed with the synchronization of the source with the following command:
```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```
**Note:** To save space and reduce download time during the synchronization process, you can also pass `--depth 1` to the `repo sync` command. However, using `--depth 1` will result in the repositories being synced without any commit history.

### Build ###

```bash

# Set up environment
 . build/envsetup.sh

# Choose a target
 lunch aosp_$DEVICE-ap4a-$BUILD_TYPE

# Build the code
 mka skyline -j$(nproc --all)
```

# Build Flags
It will be your decision and if the device supports it `true/false` any of the following flags

`You must add these flags in aosp_$device.mk`

| Flag                          |Function                       |
|-------------------------------|-------------------------------|
TARGET_BOOT_ANIMATION_RES := 1080 | Specifies the resolution of the boot animation |
TARGET_SUPPORTS_QUICK_TAP := true | Add Quick Tap feature |
SKYLINEUI_MAINTAINER := YourName  | Merge the mentioned name in the build |

# Credits:

| Projects                      |
|-------------------------------|
| **Android Open Source Project** |
| [**PixelOS**](https://github.com/PixelOS-AOSP) |
| [**LineageOS**](https://github.com/LineageOS) |
| [**DerpFest**](https://github.com/DerpFest-AOSP) |
| [**YAAP**](https://github.com/yaap) |
