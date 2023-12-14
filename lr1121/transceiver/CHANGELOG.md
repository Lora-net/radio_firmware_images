# LR1121 firmware changelog

All notable changes will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [0x0103] 2023-12-15

### Fixed

- Improve out-of-band emission glitch that may occure under certain circumstances with multiple consecutive LoRa transmissions

## [0x0102] 2023-06-29

### Added

- BPSK modulation
- Check firmware image suitability feature
- IRQ LoRa Rx timestamp

### Changed

- LoRa syncword timeout expressed in number of symbols max value changed from 255 to 65535

## [0x0101] 2023-03-13

### Added

- First public release
