# Dpak
Better Debian Package Manager

# SPDX-FileCopyrightText: no
# SPDX-License-Identifier: CC0-1.0
#
# KernOS Calamares Configuration
---

modules-search: [ local ]

instances:
  - id: desktop
    module: shellprocess
    config: shellprocess-desktop.conf

sequence:
  - show:
      - welcome
      - locale
      - keyboard
      - partition
      - packagechooser
      - users
      - summary

  - exec:
      - partition
      - mount
      - unpackfs
      - machineid
      - locale
      - keyboard
      - localecfg
      - fstab
      - initcpiocfg
      - initcpio
      - users
      - displaymanager
      - networkcfg
      - hwclock
      - services-systemd
      - initramfs
      - shellprocess@desktop
      - bootloader
      - umount

  - show:
      - finished

branding: default

prompt-install: false
dont-chroot: false
oem-setup: false
disable-cancel: false
disable-cancel-during-exec: false
hide-back-and-next-during-exec: false
quit-at-end: false
