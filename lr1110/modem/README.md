# LoRa Basics Modem-E firmware

## Known limitations

### [v1.0.7]

After a modem reset, the join-request value DevNonce, usually increasing from one join-request to the other, could decrease from 1 to 9 units. As a consequence, a join server with DevNonce verificationenabled could drop the related join requests until the value gets higher than the one before reset. This means that some join-requests will never be answered by the join server.

This limitation will be mainly evident during the modem development & evaluation phases, as device should not reset in production phase.

The workaround, only for development, is to change modem region from the one stored in flash between device reset and the Join() command is to issue the following commands between device reset and before Join() command:
1. Send `GetRegion()` to know currently stored region
1. Send `SetRegion()` command with a region different from the one returned by the modem in step 1
1. Send `SetRegion()` command with targeted region

This workaround should be used for development purpose only as it could have an impact on flash the lifetime but  **SHALL NOT** be used for production purpose.
