# Project: Trixie ARM64 Ultralight Image

This project defines a minimal Raspberry Pi OS style image build based on Debian Trixie arm64.

## What This Project Does

The config in this directory builds an ultralight image with:

- Device target: `rpizero2w`
- Image layout: `image-rpios`
- Boot partition size: `512M`
- Root partition size: `15G`
- Output image name base: `rpios-deb13-arm64-ultralight`
- Base/network layers for SSH + systemd networking + wireless support
- A local override for `rpi-device-secpolicy` that disables EEPROM update service installation for Zero 2 W

Main config file:

- `project/config/trixie-arm64-ultralight.yaml`

Local project layer files:

- `project/layer/trixie-arm64-ultralight.yaml`
- `project/layer/family-secpolicy-base-override.yaml`

Layer/variable reference document:

- `project/trixie-arm64-ultralight.md`

## Prerequisites

From the repository root, install dependencies first:

```bash
sudo ./install_deps.sh
```

Recommended host: Debian/Raspberry Pi OS compatible environment as described in the repository `README.adoc`.

## How To Build

Run from the repository root:

```bash
./rpi-image-gen build -S ./project -c trixie-arm64-ultralight.yaml
```

## Notes On Layer Override

`project/layer/family-secpolicy-base-override.yaml` declares the same layer name as the base security policy (`rpi-device-secpolicy`) so this project can customize behavior for Zero 2 W hardware.

In this project override, EEPROM updater package/service installation is removed because Zero 2 W does not have an updatable EEPROM.

**Important**: layer resolution uses the highest `X-Env-Layer-Version` for a shared layer name. Keep the project override version higher than the built-in one to ensure the override is selected.

## Build Output

The image artifact is written under `work/` in a generated image output directory.

A typical output path pattern is:

- `work/image-<image-name>/<image-name>.img`

For this config, look for image files matching:

- `work/**/rpios-deb13-arm64-ultralight*.img`

Quick check for the built image:

```bash
find ./work -type f -name 'rpios-deb13-arm64-ultralight*.img'
```
