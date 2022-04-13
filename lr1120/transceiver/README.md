# LR1120 firmware

## Driver version

The driver for this firmware is available [here](https://github.com/Lora-net/SWDR001).

| Firmware | Driver to be used                                                 |
| -------- | ----------------------------------------------------------------- |
| 0x0101   | [v2.1.1](https://github.com/Lora-net/SWDR001/releases/tag/v2.1.1) |

## Known limitations

### [0x0101]

#### High ACP (Adjacent Channel Power)

When the chip wakes up from sleep mode with retention, a parameter is not reconfigured properly. This misconfiguration can lead to an unexpectedly high adjacent channel power in all subsequent transmissions. The issue appears only in LoRa modulation, for all bandwidths except for 500kHz and 800kHz.

