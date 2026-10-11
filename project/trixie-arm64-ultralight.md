# trixie-arm64-ultralight Layer Variable Matrix

This document lists all layers used by `project/config/trixie-arm64-ultralight.yaml` (including transitive dependencies), the packages they install via `mmdebstrap.packages`, and declared config variables with defaults in `prefix.variable_name=default` form.

| Layer | Packages Installed | Variables (prefix.name=default) |
|---|---|---|
| trixie-arm64-ultralight | e2fsprogs, bash-completion, curl, iproute2, iputils-ping, less, nano, python3, systemd-cron, zstd | - |
| debian-trixie-arm64 | linux-sysctl-defaults | - |
| locale-base | console-setup | - |
| locale-config | - | locale.default=en_GB.UTF-8, locale.keyboard_keymap=gb, locale.keyboard_layout=English (UK), locale.timezone=Europe/London |
| rpi-debian-trixie | raspberrypi-archive-keyring | - |
| rpi-misc-skel | - | - |
| systemd-net-min | - | - |
| systemd-min | systemd, systemd-sysv | - |
| systemd-resolved | systemd-resolved | - |
| openssh-server | openssh-server | ssh.pubkey_user1=(empty), ssh.pubkey_only=n, ssh.host_keydir=(empty) |
| device-user-admin | sudo, login, adduser | - |
| device-user-credentials | - | device.user1=pi, device.user1pass=(empty), device.user1passhash=(empty), device.user1sudo=none, device.user1uid=(empty), device.user1gid=(empty), device.user1groups=adm,dialout,cdrom,audio,users,video,games,plugdev,input,spi,i2c,gpio,render |
| systemd-timesyncd | systemd-timesyncd | - |
| wireless-regulatory | wireless-regdb | ieee80211.regdom=00 |
| wpasupplicant | wpasupplicant | wpasupplicant.profile=(empty) |
| rpizero2w | - | device.class=zero2w, device.storage_type=sd, device.assetdir=\${DIRECTORY} |
| rpi-generic64 | - | - |
| rpi-device-base | udev, firmware-brcm80211, bluez-firmware | device.vendor=rpi, device.class=pi5, device.variant=none |
| device-base | - | device.vendor=vendor, device.class=generic, device.variant=none, device.hostname=\${IGconf_device_class}-\$(tr -dc 'a-z' < /dev/urandom | head -c 6), device.storage_type=sd, device.sector_size=512, device.assetdir=/dev/null |
| rpi-boot-firmware | - | - |
| rpi-boot-bsp | raspi-firmware | - |
| rpi-idp | - | - |
| rpi-idp-luks2 | - | device.luks2_cipher=aes-xts-plain64, device.luks2_hash=sha256, device.luks2_keysize=256 |
| rpi-device-secpolicy | ca-certificates | - |
| rpi-linux-v8 | linux-image-rpi-v8 | - |
| rpi-linux-base | - | - |
| linux-base | - | linux.page_size=4096 |
| image-rpios | initramfs-tools | image.rootfs_type=ext4, image.boot_part_size=100%, image.root_part_size=100%, image.assetdir=\${DIRECTORY}, image.disksig=random, image.devid_scheme=by-slot, image.pmap=clear |
| image-base | - | image.suffix=img, image.compression=(empty), image.version=\${IGconf_artefact_version}, image.name=rpi-\${IGconf_image_version}, image.idp_enable=n, image.pmap=(empty), image.pmap_schema=\${@IGROOT}/layer/rpi/schemas/provisionmap/v1/schema.json, image.idp_schema=\${@IGROOT}/layer/rpi/schemas/idp/v2/schema.json, image.outputdir=\${IGconf_sys_workroot}/image-\${IGconf_image_name}, image.provider=genimage, image.assetdir=/dev/null, image.bootsign_cmd=(empty), image.rootfs_type=none |
| sys-build-base | - | sys.apt_proxy=(empty), sys.apt_get_purge=y, sys.apt_keydir=\${@WORKROOT}/keys, sys.workroot=\$(realpath --canonicalize-missing ./work), sys.cachedir=\${@WORKROOT}/cache, sys.apt_cachedir=(empty), sys.buildroot=\${@WORKROOT}/build, sys.bootstrapdir=\${@WORKROOT}/bootstrap |
| sbom-base | - | sbom.enable=y, sbom.version=\${IGconf_artefact_version}, sbom.name=\${IGconf_artefact_target_name}-\${IGconf_sbom_version}, sbom.filename=\${IGconf_sbom_name}.sbom, sbom.provider=syft, sbom.syft_config=\${DIRECTORY}/syft.yaml, sbom.syft_source=(empty) |
| artefact-base | - | artefact.target_name=filesystem, artefact.version=\$(git describe --tags --always --dirty 2>/dev/null || date +%Y-%m-%d), artefact.context=chroot-\${IGconf_artefact_version} |
| target-config | - | target.context=\${IGconf_artefact_context}, target.dir=\${IGconf_sys_workroot}/\${IGconf_target_context}, target.path=\${@TARGETDIR}/\${IGconf_artefact_target_name} |
| deploy-base | - | deploy.compression=zstd, deploy.dir=\${IGconf_sys_workroot}/deploy-\${IGconf_artefact_version} |
| fs-base | - | fs.ext4_mkfs_args=(empty), fs.vfat_mkfs_args=(empty), fs.erofs_mkfs_args=(empty), fs.btrfs_mkfs_args=(empty) |
| rpi-storage-binder | udev, coreutils | storagebinder.overlay=\${DIRECTORY}/storage-binder |
