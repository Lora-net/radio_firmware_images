# LR1110 firmware

## Driver version

The driver for this firmware is available [here](https://github.com/Lora-net/lr1110_driver).

| Firmware | Driver to be used                                                                                   |
| -------- | --------------------------------------------------------------------------------------------------- |
| 0x0307   | [v7.0.0](https://github.com/Lora-net/lr1110_driver/releases/tag/v7.0.0) / v6.0.0 is also compatible |
| 0x0306   | [v5.0.1](https://github.com/Lora-net/lr1110_driver/releases/tag/v5.0.1)                             |
| 0x0305   | [v4.0.0](https://github.com/Lora-net/lr1110_driver/releases/tag/v4.0.0)                             |
| 0x0304   | [v3.0.0](https://github.com/Lora-net/lr1110_driver/releases/tag/v3.0.0)                             |
| 0x0303   | [v2.0.1](https://github.com/Lora-net/lr1110_driver/releases/tag/v2.0.1)                             |

## Known limitations

### [0x0305]

#### MAC address check for beacon in Wi-Fi acquisition mode 1 and 2 (present since 0x0303)

During the beacon MPDU extraction, the status of the comparison of the MAC addresses is overwritten by the status of the check done on the broadcast address (expected to be FF:FF:FF:FF:FF:FF). So, if the two MAC addresses are no equal but the broadcast is correct, the chip does not return an error.

#### Number of results not reset after a Wi-Fi scan command with bad parameters (present since 0x0303)

If the chip receives a Wi-Fi scan command with bad parameters, the number of results (that can be fetched with the command `WifiGetNbResults`) is equal to the number of results from the last successful Wi-Fi scan.

### [0x0304]

#### Chip hangs on `WifiReadResults` when fetching Wi-Fi basic results format

After a Wi-Fi scan, reading scan results in basic format will make the chip hangs. The only way to recover the chip is to reset it.
