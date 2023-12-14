# LR1110 firmware changelog

All notable changes will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [0x0401] 2023-12-15

### Added

- Support for GNSS scans with acquisition of satellite broadcasted time, assisted location estimation and almanac update based on satellites signal demodulation

### Fixed

- Improve out-of-band emission glitch that may occure under certain circumstances with multiple consecutive LoRa transmissions

## [0x0308] 2023-06-29

### Added

- BPSK modulation
- SubGHz Ranging feature
- Bluetooth® Low Energy Beaconing Compatibility – Tx only
- Check firmware image suitability feature
- IRQ LoRa Rx timestamp

### Changed

- LoRa syncword timeout expressed in number of symbols max value changed from 255 to 65535
- Improve robustness against 32kHz clock jitter to +/-100ppm for GNSS scan

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
