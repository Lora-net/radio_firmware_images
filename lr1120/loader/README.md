# LR1120 bootloader updater firmware

## Content

This folder contains 3 types of files:

* `*.bin` : A binary representation of the firmware image
* `*.bin.md5` : A MD5 hash of the `*.bin` sharing the same name, useful for verifying integrity of the binary file
* `*.h` : A C header file declaring an array auto-initialized with the firmware image contents

A complete reference implementation of the upgrade process is available in the [SWTL001](https://github.com/Lora-net/SWTL001) repository.

Pre-built upgrade images for the Semtech EVK/DVK (using the ST Nucleo L476 MCU) can be found in this project [Wiki](https://github.com/Lora-net/SWTL001/wiki) page.

## Description

Bootloader updater firmware is used to execute the booloader update procedure; and it cannot be used for RF operations.
Refer to AN1200.57 *LR11xx Program Memory Upgrade* for details.
