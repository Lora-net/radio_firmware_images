# LR1110 firmware

## Content

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
| 0x0401   | [v2.4.1](https://github.com/Lora-net/SWDR001/releases/tag/v2.4.1) |
| 0x0308   | [v2.3.0](https://github.com/Lora-net/SWDR001/releases/tag/v2.3.0) |
| 0x0307   | [v2.1.1](https://github.com/Lora-net/SWDR001/releases/tag/v2.1.1) |

A previous version of the driver - available [here](https://github.com/Lora-net/lr1110_driver) - has to be used for older firmware version.

| Firmware | Driver to be used                                                                                                                                                    |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0x0307   | [v7.0.0](https://github.com/Lora-net/lr1110_driver/releases/tag/v7.0.0) / [v6.0.0](https://github.com/Lora-net/lr1110_driver/releases/tag/v6.0.0) is also compatible |
| 0x0306   | [v5.0.1](https://github.com/Lora-net/lr1110_driver/releases/tag/v5.0.1)                                                                                              |
| 0x0305   | [v4.0.0](https://github.com/Lora-net/lr1110_driver/releases/tag/v4.0.0)                                                                                              |
| 0x0304   | [v3.0.0](https://github.com/Lora-net/lr1110_driver/releases/tag/v3.0.0)                                                                                              |
| 0x0303   | [v2.0.1](https://github.com/Lora-net/lr1110_driver/releases/tag/v2.0.1)                                                                                              |

## Known limitations

### [0x0305]

#### MAC address check for beacon in Wi-Fi acquisition mode 1 and 2 (present since 0x0303)

During the beacon MPDU extraction, the status of the comparison of the MAC addresses is overwritten by the status of the check done on the broadcast address (expected to be FF:FF:FF:FF:FF:FF). So, if the two MAC addresses are no equal but the broadcast is correct, the chip does not return an error.

#### Number of results not reset after a Wi-Fi scan command with bad parameters (present since 0x0303)

If the chip receives a Wi-Fi scan command with bad parameters, the number of results (that can be fetched with the command `WifiGetNbResults`) is equal to the number of results from the last successful Wi-Fi scan.

### [0x0304]

#### Chip hangs on `WifiReadResults` when fetching Wi-Fi basic results format

After a Wi-Fi scan, reading scan results in basic format will make the chip hangs. The only way to recover the chip is to reset it.
