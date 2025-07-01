# LR1120 firmware

This folder contains 3 types of files:

* `*.bin` : A binary representation of the firmware image
* `*.bin.md5` : A MD5 hash of the `*.bin` sharing the same name, useful for verifying integrity of the binary file
* `*.h` : A C header file declaring an array auto-initialized with the firmware image contents

A complete reference implementation of the upgrade process is available in the [SWTL001](https://github.com/Lora-net/SWTL001) repository.

Pre-built upgrade images for the Semtech EVK/DVK (using the ST Nucleo L476 MCU) can be found in this project [Wiki](https://github.com/Lora-net/SWTL001/wiki) page.

## Driver version

The driver for this firmware is available [here](https://github.com/Lora-net/SWDR001).

| Firmware | Driver to be used                                                 |
| -------- | ----------------------------------------------------------------- |
| 0x0201   | [v2.4.1](https://github.com/Lora-net/SWDR001/releases/tag/v2.4.1) |
| 0x0102   | [v2.3.0](https://github.com/Lora-net/SWDR001/releases/tag/v2.3.0) |
| 0x0101   | [v2.1.1](https://github.com/Lora-net/SWDR001/releases/tag/v2.1.1) |

## Known limitations

### [0x0101]

#### High ACP (Adjacent Channel Power)

When the chip wakes up from sleep mode with retention, a parameter is not reconfigured properly. This misconfiguration can lead to an unexpectedly high adjacent channel power in all subsequent transmissions. The issue appears only in LoRa modulation, for all bandwidths except for 500kHz and 800kHz.
