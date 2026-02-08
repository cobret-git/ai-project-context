# Changelog

All notable changes to this project will be documented in this file.

## [1.1.0] - 2025-02-08

### Added
- `.aiignore` support — a separate ignore file for excluding tracked files from AI context
- New `-AiIgnoreFileName` parameter to customize the ignore file name
- Filtering is now two-pass: .gitignore first, then .aiignore

### Changed
- Simplified README
- Extracted shared pattern-reading logic into `Read-IgnorePatterns` helper

## [1.0.0] - 2024-12-19

### Added
- Initial release
- Universal project context generation
- Automatic .gitignore parsing
- Binary file detection
- 40+ language support
- Auto repository root detection
- Configurable output location