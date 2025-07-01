# LoRa Basics Modem-E v2 firmware

## Content

This folder contains 3 types of files:

* `*.bin` : A binary representation of the firmware image
* `*.bin.md5` : A MD5 hash of the `*.bin` sharing the same name, useful for verifying integrity of the binary file
* `*.h` : A C header file declaring an array auto-initialized with the firmware image contents

A complete reference implementation of the upgrade process is available in the [SWTL001](https://github.com/Lora-net/SWTL001) repository.

Pre-built upgrade images for the Semtech EVK/DVK (using the ST Nucleo L476 MCU) can be found in this project [Wiki](https://github.com/Lora-net/SWTL001/wiki) page.

## Description

LoRa Basics Modem-E offers seamless embedding of the LoRaWAN stack into LR1121 chip. Once flashed on the LR1121, the binary code of Modem-E offers:

* Fully featured stack with all classes (A/B/C)
* all regional parameters and WW2G4
* CSMA/LBT
* Relayed end-device (i.e. Relay Tx)
* Multicast class B/C
* FUOTA (one fragmentation session is supported)
* The possibility to co-host on the same sensor LoRaWAN and proprietary protocol leveraging state of the art RF performances of LR1121.

## Driver version

The driver for this firmware is available here [https://github.com/Lora-net/lr1121_modemE_driver](https://github.com/Lora-net/lr1121_modemE_driver).

| Firmware | Driver to be used                                                             |
| -------- | ----------------------------------------------------------------------------- |
| v2.0.1   | [v1.0.0](https://github.com/Lora-net/lr1121_modemE_driver/releases/tag/v1.0.0) |

## Known limitations

### [v2.0.1]

#### Transceiver mode

When used in Transceiver (Suspend) mode, the chip might get stuck in Sleep mode if SetSleep command is called with RTC mode set to 0 (XTAL) and no timeout is set.

Workaround:

If running any application with Modem-e in TRX mode (for legacy protocols), make sure that ${\textsf{\color{red} SetSleep() command is used with RTC mode set to 1 and a timeout is set.}}$

Note that the existing transceiver driver contains this workaround

#### FUOTA

A single fragmentation session is supported. Fragmented Data Block, frag_index must be set to 0

#### LoRaWAN

#### TxParamSetupReq only active after LinkADRReq

MaxEIRP requested by the MAC command TxParamSetupReq will only be applied after the LinkAdrReq is received. LinkAdrReq must set power between 0x0 and 0xE.. This only affects AS923, AU915 and WW2G4 regions.

Workaround : make sure that the LNS sends LinkAdrReq (with power set between 0x0 and 0xE) right after TxParamSetupReq to operate with the proper power level.

#### LinkADRReq behavior with network ADR disabled

When the modem-E is configured with network ADR disabled, and receives a LinkADRReq from the network nonetheless, the modem will accept it and apply the included ChMask, but it will refuse the power and the datarate settings even if the value is 0xF (in normal case 0xF should be accepted). It should discard the entire command but does not.

Workaround: Modem-e is NOT expecting to receive LinkADRReq when it is declaring itself as ADR disabled. Make sure the LNS behaves accordingly.

#### Join Data Rate distribution might erroneously be used for normal traffic after Join

The modem keeps the JoinDatarate distribution after it has joined in two cases:

* when the CSMA or LBT detect a possible collision during the first joinReq
* when the user leaves before the end of a join attempt, then tries to join again

Workaround: On Join success Event set your ADR profile systematically

#### Get regional duty-cycle

For region with duty-cycle constraint, if transmit time is available and the Relay Tx is disabled, the function to get the duty-cycle status return 0 instead of available time

#### Modem-e at 2.4GHz

In modem mode with 2.4GHz path the -18dBm is not usable, if used it will result in undetermined behavior

Workaround: ensure that the LNS doesn’t request -18 dBm output power.
