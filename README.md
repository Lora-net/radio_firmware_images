# radio_firmware_images

This repository contains _radio chip firmware_ files sorted by radio chip and types of firmwares (transceiver or modem).
For each existing combination can be found 3 files:

* `*.bin` : A binary representation of the firmware image (Do not drag and drop!)
* `*.bin.md5` : A MD5 hash of the `*.bin` sharing the same name, useful for verifying integrity of the binary file
* `*.h` : A C header file declaring an array containing the firmware image

A complete reference implementation of the upgrade process is available in the [SWTL001](https://github.com/Lora-net/SWTL001) repository.

Pre-built upgrade images for the Semtech EVK/DVK (using the ST Nucleo L476 MCU) can be found in this project [Wiki](https://github.com/Lora-net/SWTL001/wiki) page.
