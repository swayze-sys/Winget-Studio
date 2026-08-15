# Changelog

All notable user-facing changes are documented here.

## 2.02 — 2026-08-15

### Discovery and provider search

- Searches from **Discover apps → All sources** now start WinGet and every available additional provider concurrently.
- Each additional provider performs its catalog search and installed-package lookup concurrently.
- Provider failures remain isolated so successful results from other sources are preserved.
- Chocolatey now uses a chocolate-bar symbol in the Provider column.
- Bumped the application and installer to 2.02 so existing 2.01 installations detect the release as an update.
- Fixed release-tag normalization for GitHub tags written as either `v2.02` or `v.2.02`; the compatible `v2.02` release is published as Latest for installed 2.01 clients.
- Verified the release build with all 87 automated tests.

## 2.01 — 2026-08-14

### Updates and elevation

- The main application remains in the user context while administrative updates are delegated to a session-bound elevated helper.
- The UAC and IPC handshake runs outside the UI thread so the main window remains responsive while elevation is requested.
- Machine-wide WinGet packages remain available to the elevated helper even when its catalog differs from the user-scoped catalog.
- The main executable uses `asInvoker` by default. Administrator mode is an explicit setting and first-run choice.

### Update reliability

- Wrapped or malformed WinGet source values are normalized before they are reused with `--source`.
- Successful `--include-unknown` runs are recognized from update history so the same package is not immediately offered again after a catalog refresh.
- The Update Advisor recognizes manufacturer-log messages that report the same or a newer version already installed, as well as cases where no upgrade is available.
- Per-package suppressions are stored in `update-suppressions.json` and automatically expire when WinGet reports a different available version.
- Confirmed Winget Studio updates are downloaded from an HTTPS feed, checked with SHA-256, and applied by the existing installer through `/update /launch`.

### Installer and interface

- The offline bundle includes the available .NET Runtime 10 x64 when the official Microsoft download can be obtained and Authenticode-verified during the build; otherwise setup downloads the signed runtime when needed.
- The bundle builder accepts versioned runtime filenames and stores them under a stable bundle name.
- The Settings window is standardized at 1248 × 920.
- A dedicated Updates tab can check for Winget Studio releases at startup or on demand.
- Rebuilt the setup bootstrapper with the correct `v.2.01` GitHub asset URLs embedded, then republished the online installer, offline bundle, manifest, and build metadata with matching SHA-256 digests.

## 1.9.9 — 2026-08-13

- Added a light theme using the same translucent glass design language as the dark theme.
- Added an optional Release Notes action that prefers WinGet release-note metadata and falls back to the publisher homepage.
- Added parsing and caching for release-note, homepage, and publisher URLs.
- Expanded automated coverage to 77 unit tests.

## 1.9.8 — 2026-08-13

- Split large view-model and window implementations into partial classes without changing behavior.
- Added broad unit-test coverage for parsing, restart continuation, the Update Advisor, repository matching, version detection, discovery, and process output.
- Restored the Notification Host to the expected release directory layout.

## 1.9.7 — 2026-08-13

- Changed diagnostic exports to semicolon-separated UTF-8 CSV with anonymized user paths.
- Parallelized package searches across configured sources, with failures isolated per source.
- Added relevance filtering and provider-aware sorting to search results.
- Refined selection placement in card and list views.

## Earlier milestones

- **1.9.6:** Diagnostic export, robust WinGet parsing, parallel update detection, and installer modernization.
- **1.9.5:** Configurable Thin Acrylic appearance and coordinated translucent surfaces.
- **1.9.4:** Separate least-privilege Notification Host.
- **1.9.3:** Windows App SDK runtime diagnostics, repair, and test notifications.
- **1.9:** Update cancellation, scheduling, restart continuation, process blocking, additional providers, and signature status.
- **1.8:** Update Advisor, controlled reinstall workflow, and local executable version detection.
- **1.7:** Selectable process output, installer logs, history, and contextual error guidance.
- **1.6:** Application discovery, additional package providers, and installed-program management.
- **1.5:** Acrylic interface, list view, configurable columns, and live status.
- **1.4:** Selective import/export, settings, pins, and source management.
- **1.3:** Confirmed elevation and multi-package updates.
- **1.2:** Per-application update actions, sorting, and filters.
- **1.1:** Robust WinGet parsing and package/version/source display.
- **1.0:** Initial WinUI 3 application with selective WinGet updates and process logging.
