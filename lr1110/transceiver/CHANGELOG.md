# LR1110 firmware changelog

All notable changes will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [0x0307] 2021-09-22

### Added

- `GetLoraRxHeaderInfos()` to get information from LoRa header in Rx mode
- `GnssGetSvVisible()` to get the number of visible space vehicles based on given assistance data

### Changed

- Result mask format in `GnssAutonomous()` and `GnssAssisted()`

### Removed

- `GnssScanContinuous()`
- GNSS scan mode 1 - "Dual scanning"

## [0x0306] 2021-07-20

### Added

- Wi-Fi acquisition mode 5 – SSID beacon search mode
- `DriveDiosInSleepMode` to control the behavior of RF switch and IRQ line DIOs ins sleep mode

### Fixed

- CRC calculation on SPI frame when reading data on MISO during a write command
- MAC address check for beacon in Wi-Fi acquisition mode 1 and 2
- Number of results not reset after a Wi-Fi scan command with bad parameters

## [0x0305] 2021-04-07

### Changed

- Added current Wi-Fi channel information to Wi-Fi extended full results
- Improved GNSS almanac management

### Fixed

- Chip hangs on `WifiReadResults` when fetching Wi-Fi basic results format

## [0x0304] 2021-01-13

### Changed

- Enhanced FCC compliance for transient emissions in non-restricted bands

## [0x0303] 2020-10-10

### Added

- First public release
