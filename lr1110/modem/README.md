# LoRa Basics Modem-E firmware

## Driver version

The driver for this firmware is available [here](https://github.com/Lora-net/lr1110_modem_driver).

| Firmware | Driver to be used                                                             |
| -------- | ----------------------------------------------------------------------------- |
| v1.1.8   | [v3.1.0](https://github.com/Lora-net/lr1110_modem_driver/releases/tag/v3.1.0) |
| v1.1.7   | [v3.0.1](https://github.com/Lora-net/lr1110_modem_driver/releases/tag/v3.0.1) |
| v1.0.7   | [v2.0.1](https://github.com/Lora-net/lr1110_modem_driver/releases/tag/v2.0.1) |

## Known limitations

### [v1.1.8]

#### Index values for file upload initialization command (present since v1.0.7)

Only index values from 1 to 223 are allowed.

#### Power emission for ARIB (present since v1.1.7)

For ARIB, power emission must be typically set to 9dBm by setting the power offset during the JOIN procedure using SetTxPowerOffset command during the device configuration phase after Reset as explained in the Reference Manual documentation.

#### FPort value when using the stream service (present since v1.0.7)

The parameter `FPort = 0` (i.e. put the stream in a DM frame) can lead to an undefined behavior of the stream service and must not be used. Make sure you explicitly use the DM FPort value if you want to send a stream as a DM frame. This limitation is also impacting previous version of the firmware.

#### File upload service with encryption mode enabled (present since v1.0.7)

The file upload service cannot be used with encryption mode enabled. If data encryption in required, the user has to encrypt the file at the application level and then send it through the file upload service.

#### Number of retransmission (present since v1.0.7)

The number of retransmission cannot be set greater than 7. If value higher than 7 is required, it is recommended to retransmit the packet at the application level. For instance, if an overall number of retransmission of 13 is required, the user has to send two packets with the number of retransmission set to 8.

#### Constellation to scan after a partial GNSS almanac update (present since v1.0.7)

A partial GNSS almanac update will modify the constellation to scan parameter. As a workaround, the user has to reconfigure this parameter just before launching a GNSS scan.

#### ADR fallback with uplink dwell time activated (present since v1.1.7)

For AS923 and AU915 regions, the ADR fallback is equal to DR1 or DR0 when the uplink dwell time is activated: the modem cannot send uplink frames anymore.

#### Modem crash in region RU864 (present since v1.1.7)

When receiving a NewChannelReq MAC command in RU864 region, the modem crashes.


### [v1.1.7]

#### High ACP (Adjacent Channel Power) (present since v1.0.7)

When the chip wakes up from sleep mode with retention, a parameter is not reconfigured properly. This misconfiguration can lead to an unexpectedly high adjacent channel power in all subsequent transmissions.

The issue appears only in LoRa modulation, for all bandwidths except for 500kHz.


### [v1.0.7]

#### DevNonce

After a modem reset, the join-request value DevNonce, usually increasing from one join-request to the other, could decrease from 1 to 9 units. As a consequence, a join server with DevNonce verification enabled could drop the related join requests until the value gets higher than the one before reset. This means that some join-requests will never be answered by the join server.

This limitation will be mainly evident during the modem development & evaluation phases, as device should not reset in production phase.

The workaround, only for development, is to change modem region from the one stored in flash between device reset and the Join() command is to issue the following commands between device reset and before Join() command:

1. Send `GetRegion()` to know currently stored region
1. Send `SetRegion()` command with a region different from the one returned by the modem in step 1
1. Send `SetRegion()` command with targeted region

This workaround should be used for development purpose only as it could have an impact on flash the lifetime but  **SHALL NOT** be used for production purpose.

#### Frame counter

In the case `nb_trans` > 1, if duty cycle limit is reached before the end of the sequence (`nb_trans` is reached or a reception occurs), the frame counter of the next packet is not incremented.

#### Data-rate profile

If the data-rate profile is updated by the network, the data returned by the `GetAdr()` command is not consistent.

#### Watchdog

If the internal watchdog is triggered during a radio operation (transmission, reception, GNSS or Wi-Fi scan), it is ignored. The user has to make sure that a watchdog is running on the application side.

#### GetCharge

The command `GetCharge()` returns erroneous values.
