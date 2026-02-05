# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.2.1] - 2026-02-05
- Add CHANGELOG.md

## [2.2.0] - 2026-02-05

### Changed
- Merged branch improvements from 1.x
- Updated docker-compose configuration with enhanced settings
- Added new environment variable configuration
- Removed "web" entrypoint

### Files Modified
- `.example-env`: Added new configuration option
- `docker-compose.yml`: Enhanced service configuration (13 additions, 5 deletions)

## [2.1.1] - 2026-01-28

### Added
- Implemented shared volume as configurable variable

### Changed
- Made shared volume configuration more flexible through environment variables

### Files Modified
- `.example-env`: Added shared volume variable
- `docker-compose.yml`: Updated to use shared volume variable

## [2.1.0] - 2026-01-23

### Changed
- Adjusted Varnish port configuration
- Updated port mappings for better service integration

### Files Modified
- `docker-compose.yml`: Modified Varnish port settings

## [1.1.0] - 2025-12-19

### Changed
- Updated base image version to 1.1.0
- Improved base image stability and features

### Files Modified
- `docker-compose.yml`: Updated base image version references

## [1.0.1] - 2025-12-16

### Changed
- Set to latest stable WissKI version
- Improved stability by using stable release

### Files Modified
- `docker-compose.yml`: Updated WissKI version to stable release

## [1.0.0] - 2025-12-16

### Added
- Initial stable release
- Production-ready Varnish configuration

### Changed
- Use stable Varnish version for production deployment
- Added production environment configuration

### Files Modified
- `.example-env`: Added production configuration
- `docker-compose.yml`: Updated to stable Varnish version

---

## Release Notes

This project follows semantic versioning:
- **Major version** (X.0.0): Breaking changes or major feature additions
- **Minor version** (X.Y.0): New features, backwards compatible
- **Patch version** (X.Y.Z): Bug fixes, backwards compatible

For more information about each release, see the corresponding git tags in the repository.
