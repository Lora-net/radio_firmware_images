# Modem-e v2.x.x CHANGELOG

## Modem-e v2.1.0 (2026-04-03)

### Changes
* [Modem] Update LoRaWAN stack with LoRa Basic Modem v4.9.1
* [Modem] Reset Event does not return reset counter anymore

### Add
* [Modem] LoRaWAN ABP support with save/restore ram context in NVM
* [LoRaWAN] possibility to update LoRaWAN channel Mask before sending uplinks
* [Modem] Event SMTC_MODEM_EVENT_NO_DOWNLINK_THRESHOLD and associated commands
* [Modem] Event SMTC_MODEM_EVENT_RESET_REQUEST when the modem need to be reset, for example the LoRaWAN certification could request a DUT reset

### Fixes
* [Modem] CMD_TST_TX_LORA the syncword was ignored and not applied

### Security

Refer to [Semtech security bulletin](https://www.semtech.com/company/security/security-bulletins).

- CVE-2025-14857
- CVE-2025-14858
- CVE-2025-14859

## Modem-e v2.0.2 (2025-08-25)

### Changes

* [LfClock] Configuration: The LfClock configuration is no longer stored in flash memory. The recommended workaround for the transceiver is to set the LfClock to RC_32KHz before calling `SetSleep` without a timer. This workaround is now valid for Modem-e v2.0.2

* [Modem] Crystal Error: The Modem-e boots with a crystal error set to 16000 ppm.

### Fixes

* [Trx] SPI command timeout: The radio operation fails after 2 seconds due to a timeout.
* [Modem] 2.4GHz path: The transmission at -18dBm is now usable.
* [Modem] rand() function function has been rewritten for better randomness
* [LoRaWAN] TxParamSetupReq: The transmission power is adjusted to the new requested value if it's lower than the previous one.
* [LoRaWAN] LinkADRReq: Proper handling when network ADR is disabled.
* [LoRaWAN] Duty-cycle restriction now takes into account time spent in sub-band centered at 869.3 MHz
* [LoRaWAN] Compute duty-cycle for LR-FHSS based on the center frequency
* [LoRaWAN] compute statistics after LR-FHSS hopping to measure the right TOA
* [LoRaWAN] SNR and RSSI for FSK modulation returned by the stack were not correct in class A/B/C
* [LoRaWAN] Workaround to reach the radio sensitivity in case of LR11xx + bandwidth BW500
* [ADR] Join datarate distribution: No longer retained after joining the network if a collision is detected during LBT or CSMA.
* [FUOTA] Fragmented Data Block: `frag_index` is checked to prevent overruns.
* [FUOTA] FragDecoder.Status.MissingFrag: Was not computed correctly on successful file reconstruction because it was calculated after the return success.
* [FUOTA] FragSessionStatusAns, if FragIndex is invalid, MICError and MemoryError bits are 0.
* [FUOTA] Multicast package can now be used with WW_2G4 region
* [Relay] Tx: force compute WOR MIC after enablement or join accept, the MIC was wrong if the end-device had joined without a relay
* [Relay] Tx: MAC parse must check valid Rx datarate for second channel and not Tx datarate, specifically for FCC region.
* [TestMode] remove BW check constraint to be able to use BW 7KHz
* [TestMode] Allow smtc_modem_get_charge() in test mode