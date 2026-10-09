# LR1121 firmware changelog

All notable changes will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [0x0105] 2026-10-12

### Security

Refer to [Semtech security bulletin](https://www.semtech.com/company/security/security-bulletins).

- CVE-2026-6232

## [0x0104] 2026-04-01

### Added

- Low latency APIs

### Security

Refer to [Semtech security bulletin](https://www.semtech.com/company/security/security-bulletins).

- CVE-2025-14857
- CVE-2025-14858
- CVE-2025-14859

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
