# Winget Studio

Winget Studio is a WinUI 3 desktop application for discovering, installing, updating and diagnosing Windows applications through WinGet and additional package providers.

**Current release:** 2.10.0 · [Latest release](https://github.com/swayze-sys/Winget-Studio/releases/latest) · [Deutsch](README.de.md)

## Highlights

- Search WinGet, Chocolatey, npm, pip/PyPI, .NET Tool and PowerShell Gallery independently, with concurrent provider searches and live status.
- Review installed and available versions in card or sortable list views, select one or many packages, and follow command output, progress and exit codes.
- Use the Update Advisor for common WinGet, installer, process, pin, network and file-lock failures.
- Keep a searchable, selectable, copyable and CSV-exportable update history with complete failure details.
- Configure sources, pins, filters, scheduled runs, update channels, language, appearance and diagnostic retention.
- Inspect package details, publisher information, release notes, trust/signature state and installation paths.
- Use the Fleet management area for device registration, embedded NetworkDeepscan discovery, device groups and policies, agent status, inventory, inspection and targeted updates.
- The HTTPS Fleet Agent returns heartbeat, user, operating system, network identity, software inventory, progress, logs and update results. WinRM/WinRS/DCOM remain explicit diagnostic fallbacks.
- Inspect a registered device in a dedicated view with overview, agent diagnostics, protocol and a client-style Programs view with search, icons, columns, selection and WinGet updates.
- Fleet data is kept locally in `%LOCALAPPDATA%\\WingetStudio\\fleet-devices.json`; the agent stores inventory, settings and logs on the target under `%PROGRAMDATA%\\WingetStudio\\FleetAgent`.

See the [Fleet management documentation](https://github.com/swayze-sys/Winget-Studio-Source/blob/fleet-management/Documentation/Fleet-Management.en.md) for registration, communication, inventory and diagnostics. Large-scale server orchestration and formal critical-update approvals remain planned expansions; 2.10.0 focuses on reliable single-device Fleet operations.

## Requirements

- Windows 10 build 19041 or later; Windows 11 is recommended.
- x64 system with WinGet / Microsoft App Installer.
- .NET 10 Desktop Runtime and Windows App SDK Runtime as required by the installer.
- Optional provider tools (Chocolatey, Node.js/npm, Python/pip, .NET SDK or PowerShellGet) for their respective catalogs.

## Installation

Download the current setup from [GitHub Releases](https://github.com/swayze-sys/Winget-Studio/releases/latest). The offline bundle contains the payload and can be extracted before running `WingetStudio-Setup.exe`; the web setup downloads and verifies the same payload. The installer performs SHA-256 validation, preserves user data during updates and offers the optional Fleet Agent component.

## Updates

Winget Studio checks the configured GitHub stable or pre-release channel and applies confirmed updates through the existing installer. The updater never replaces individual application files.

## Privacy and local data

Winget Studio stores settings, icon cache, update history and Fleet data locally. It sends no telemetry. The Fleet Agent stores its inventory, settings and logs under `%PROGRAMDATA%\\WingetStudio\\FleetAgent`.

## Release history

See [CHANGELOG.md](CHANGELOG.md) for the complete release history.

Winget Studio is authored and maintained by **Sven Philipp**.
