# LoRa Basics Modem-E firmware changelog

## Modem-e v2.1.0 (2026-04-03)

From version 2.1.0+, Modem-E V2 has been ported to the LR1110 as well. The two chips share the exact same LoRaWAN stack.
On the LR1110, it is not possible to use GNSS and WIFI functionalities with the latest Modem-E V2 firmware installed.

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

## [v1.1.9] 2024-02-29

### Fixed

- PLL unlocking and spurs on the start of the LoRa modem

## [v1.1.8] 2022-05-20

### Fixed

- High ACP (Adjacent Channel Power)  (see PCN-000822)

## [v1.1.7] 2021-05-11

### Added

- AS923 (3 sub-regions included), IN865, KR920, RU868 and AU915 LoRaWAN regional parameters
- LoRaWAN class C
- Listen-Before-Talk (LBT) - activation / deactivation and threshold duration / bandwidth configuration
- Stream redundancy configuration - from 0% (i.e. no redundancy) up to 110%
- NbTrans parameter configuration for all ADR profiles but network-controlled
- RTC compensation
- Crashlog

### Changed

- Duty cycle management
- __BREAKING CHANGE__: Response of `GetStatusDutyCycle()` that returns transmit duty cycle status has been changed compared to v1.0.7

## [v1.0.7] 2020-10-10

### Added

- First public release
