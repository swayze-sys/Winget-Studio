## Fleet development branch — 2.10.0 (private, unreleased)

The private fleet-management branch documents and implements the Fleet management work separately from the public client release line.

- Dedicated Fleet window with device registration, embedded NetworkDeepscan discovery, device database, groups, policies, rollouts, protocol/debug and Audit/Advisor areas.
- Self-contained HTTPS Fleet Agent on port 8765 with heartbeat status, inventory, progress, logs, configuration and targeted updates.
- Agent-first communication with WinRM, WinRS and DCOM as explicit diagnostics fallbacks.
- Device inspection with a client-style Programs view, icons, search, selection, columns, details and WinGet updates.
- Complete Fleet/Agent diagnostics with searchable, scrollable, selectable, copyable and exportable logs.

## 2.10.0 — 2026-08-16 (Fleet management, agent inventory and diagnostics)

### Fleet management
- Added a dedicated Fleet window with overview, devices, groups and policies, rollouts, protocol/debug and audit/advisor areas.
- Registered devices are stored in a local Fleet database with stable identity de-duplication, selectable columns, sorting, filters and persistent protocol data.
- Network Discovery uses the embedded NetworkDeepscan PowerShell script and exposes IP, MAC, vendor, DNS/NetBIOS, ICMP, SMB, device type, confidence and detection reason.
- Device inspection includes an overview, live agent diagnostics, protocol and a Programs view with search, cards/list mode, icons, details, selection, column controls and targeted updates.

### Fleet Agent and remote communication
- Added a self-contained HTTPS Fleet Agent on port 8765 with tray status, Start-menu integration, heartbeat and inventory settings.
- Agent-first status and inventory calls return user, OS, IP, MAC, vendor, device type, software inventory, progress, logs and update results. WinRM, WinRS and DCOM remain diagnostic fallbacks.
- Fleet logs and agent log files are searchable, scrollable, selectable, copyable and exportable; complete STDOUT, STDERR, exit codes and stack traces are retained for failures.
- Agent update requests now use the same web-JSON conventions as the client, preventing valid package IDs from being deserialized as an empty request.

### Inventory, icons and update reliability
- WinGet is the primary inventory provider; Registry is an explicitly labelled fallback.
- Remote package icons are transferred as embedded data and materialized in the local Fleet icon cache; missing Simple Icons are recorded as `.missing` discovery markers.
- Long-running inventory operations report phase, detail and percentage progress until the agent finishes.
- Version formatting keeps semantic versions such as 2.10.0 intact while retaining legacy 2.08 display compatibility.

## 2.07 – Quellenverwaltung und Quellenaktualisierung

- Quellen aktualisieren verarbeitet WinGet-Quellen einzeln und meldet fehlerhafte Quellen mit Namen.
- Quellenverwaltung gruppiert WinGet sowie zusätzliche Provider-Standardquellen.
- NuGet.org ist standardmäßig aktiviert; das Einstellungsfenster wurde für die erweiterte Liste vergrößert.

## 2.06 – UI- und Parserkorrekturen

- About-Dialog mit sichtbarem Logo und direkter Updateprüfung.
- Providerstatus vollständig und kompakt; fehlerhafte Provider-Kodierung entfernt.
- Auswahl im Updateverlauf optisch hervorgehoben.
- WinGet-Versionsparser korrigiert, damit verschobene Tabellenspalten keine doppelten Versionswerte erzeugen.
- Theme-Schalter leicht nach links versetzt.

## 2.05 – Provider-Auswahl, Verlaufsexport und Update-Regeln

- Provider-Auswahl als kompaktes Dropdown mit Checkboxen direkt neben der Suchleiste.
- PowerShell Gallery nutzt die öffentliche Gallery-API; Status und Fehler werden nachvollziehbar angezeigt.
- Updateverlauf: Zeilen auswählen, vollständige Fehlermeldungen kopieren und alle Spalten als CSV exportieren.
- Gespeicherte Aussetzungen pro Programm werden unter Update-Regeln aufgelistet und können entfernt werden.
- Einstellungen: Tab „Erweitert“, größere Standardgröße, 7-Tage-Aufbewahrung und 90 Tage als Standard.
- Tabellenlayout für Version/Exit-Code verbessert; Parser verhindert, dass Quellen in Versionswerte laufen.
- About-Dialog mit großem Winget-Studio-Logo.

# Changelog

All notable user-facing changes are documented here.

## 2.04 — 2026-08-15

### Discovery and provider control

- Provider checkboxes select WinGet, Chocolatey, npm, pip/PyPI, .NET Tool and PowerShell Gallery independently.
- Live provider status shows search progress, result count, elapsed time, cache use, unavailable providers and failures while all selected sources continue to run concurrently.

### Package details and trust

- A new Discover details action loads publisher, description, project page, license, release notes, installer type, architecture and release date from WinGet where available.
- External providers link directly to their package pages.
- Trust guidance distinguishes Microsoft Store packages, WinGet manifests and community providers without claiming that a not-yet-downloaded installer signature has been verified.

### Update preview and setup

- Single and multi-package updates show planned version changes, sources, publishers, running processes and active installer options before elevation or execution.
- App setup no longer asks for a language in `/update` mode; it reuses the saved installer language and falls back to the Windows UI language.
- Verified the clean release with all 91 automated tests.

## 2.03 — 2026-08-15

### App update reliability

- Each setup download now uses a unique temporary directory, preventing automatic and manual checks or multiple processes from locking the same installer path.
- Installer targets are created exclusively and existing files are never silently overwritten.
- Fixed the clean publish pipeline so WinUI XBF/PRI resources, the Admin Helper, and the Notification Host are always included.
- Version 2.03 is a real version increment, allowing installed 2.02 builds to detect the updater correction.
- Added a one-time compatibility feed that lets affected 2.01 installations bypass their legacy digest-lock bug and update directly to 2.03.
- Verified the corrected release with all 88 automated tests.

## 2.02 — 2026-08-15

### Discovery and provider search

- Searches from **Discover apps → All sources** now start WinGet and every available additional provider concurrently.
- Each additional provider performs its catalog search and installed-package lookup concurrently.
- Provider failures remain isolated so successful results from other sources are preserved.
- Chocolatey now uses a chocolate-bar symbol in the Provider column.
- Bumped the application and installer to 2.02 so existing 2.01 installations detect the release as an update.
- Fixed release-tag normalization for GitHub tags written as either `v2.02` or `v.2.02`; the cache-distinct `v2.02-final` release is published as Latest for installed 2.01 clients.
- Closed the downloaded setup file before SHA-256 verification so the updater no longer blocks its own integrity check.
- Added a process-only compatibility feed for the one-time update from affected 2.01 installations; normal 2.02 starts continue to use the standard latest-release endpoint.
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
