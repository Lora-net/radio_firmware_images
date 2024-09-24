# LoRa Basics Modem-E firmware changelog

All notable changes will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

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
