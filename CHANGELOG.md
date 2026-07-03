# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [3.3.0] - 2026-07-03

### Changed
- Default Redis image from `7.4-alpine` to `8-alpine` (configurable via `REDIS_IMAGE_VERSION`)

### Files Modified
- `docker-compose.yml`: Redis image version variable
- `.example-env`: Document `REDIS_IMAGE_VERSION`

## [3.2.0] - 2026-07-03

### Added
- Traefik `rate-limit-high@docker` on external Varnish and `raw.*` Drupal routers; internal bypass routers for Docker CIDRs (priority 100)

### Changed
- Tighten Drupal healthcheck: 15s interval, 30 retries, 120s start period

### Fixed
- Rename Varnish image version variable from `SCS_VARNISH_IMAGE_VERSION` to `VARNISH_IMAGE_VERSION` (matches `.example-env`)

### Files Modified
- `docker-compose.yml`: Rate-limit middleware, internal bypass routers, healthcheck tuning, Varnish image version env var name

## [3.1.0] - 2026-06-15

### Changed
- Default `DRUPAL_PROXY_ADDRESSES` to `auto` (auto-detect Docker network CIDRs from container interfaces; recommended behind Traefik/Varnish)

### Files Modified
- `docker-compose.yml`: Default proxy addresses to `auto`
- `.example-env`: Document `DRUPAL_PROXY_ADDRESSES` options

## [3.0.0] - 2026-06-10

### Changed
- Replace the `drupal-root` volume with two volumes: `drupal-sites` (`/opt/drupal/web/sites`) and `drupal-private-files` (`/opt/drupal/private-files`); the codebase is immutable in the 3.x base image (breaking: 2.x `drupal-root` volumes are not compatible, migrate `web/sites` and private files manually)
- Default `DRUPAL_PRIVATE_FILES_DIR` to `/opt/drupal/private-files` (outside the web root)
- `WISSKI_STARTER_VERSION` and `WISSKI_DEFAULT_DATA_MODEL_VERSION` now act as recipe apply flags (non-empty = apply); module and recipe versions are baked into the image via the drupal_packages manifest

### Files Modified
- `docker-compose.yml`: New volume layout, recipe flag defaults, private files default

## [2.4.0] - 2026-3-17

### Added
- Add Nextcloud connection environment variables: `NEXTCLOUD_BASE_URL`, `NEXTCLOUD_LOGIN_NAME`, `NEXTCLOUD_APP_PASSWORD`

### Changed
- Remove shared volume (`scs--shared-data`) and `/var/private-files` mount from drupal service

### Files Modified
- `docker-compose.yml`: Replace shared volume with Nextcloud env vars, remove external volume definition

## [2.3.0] - 2026-02-05

### Added
- Add `KEYCLOAK_URL` environment variable for configurable OpenID Connect auth URL

### Files Modified
- `docker-compose.yml`: Pass KEYCLOAK_URL to drupal service

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
