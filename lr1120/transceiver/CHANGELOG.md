# LR1120 firmware changelog

All notable changes will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [0x0201] 2023-12-15

### Added

- Support for GNSS scans with acquisition of satellite broadcasted time, assisted location estimation and almanac update based on satellites signal demodulation

### Fixed

- Improve out-of-band emission glitch that may occure under certain circumstances with multiple consecutive LoRa transmissions

## [0x0102] 2023-06-29

### Added

- BPSK modulation
- SubGHz Ranging feature
- Bluetooth® Low Energy Beaconing Compatibility – Tx only
- Check firmware image suitability feature
- IRQ LoRa Rx timestamp

### Changed

- LoRa syncword timeout expressed in number of symbols max value changed from 255 to 65535
- Improve robustness against 32kHz clock jitter to +/-100ppm for GNSS scan

## [0x0101] 2022-04-13

### Added

- First public release
