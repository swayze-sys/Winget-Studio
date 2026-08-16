# Winget Studio

Winget Studio is a WinUI 3 desktop application for discovering, installing, updating and diagnosing Windows applications through WinGet and additional package providers.

**Current public release:** 2.08.5 · [Latest public release](https://github.com/swayze-sys/Winget-Studio/releases/latest) · [Deutsch](README.de.md)

## Highlights

- Search WinGet, Chocolatey, npm, pip/PyPI, .NET Tool and PowerShell Gallery independently, with concurrent provider searches and live status.
- Review installed and available versions in card or sortable list views, select one or many packages, and follow command output, progress and exit codes.
- Use the Update Advisor for common WinGet, installer, process, pin, network and file-lock failures.
- Keep a searchable, selectable, copyable and CSV-exportable update history with complete failure details.
- Configure sources, pins, filters, scheduled runs, update channels, language, appearance and diagnostic retention.
- Inspect package details, publisher information, release notes, trust/signature state and installation paths.

## Fleet development branch

The complete Fleet management implementation is maintained separately in the private Winget-Studio-Source repository on the fleet-management branch. Its 2.10.0 development documentation covers:

- Device registration and embedded NetworkDeepscan discovery with IP, MAC, vendor, DNS/NetBIOS, ICMP, SMB, device type and confidence.
- A local device database with stable identity de-duplication, groups, policies, rollouts, filters, selectable columns and persistent protocols.
- HTTPS Fleet Agent communication on port 8765 with live heartbeat, operating-system/user/network data, software inventory, progress, logs and targeted WinGet updates.
- Device inspection with a client-style Programs view, inventory refresh progress, icons, details, selection and diagnostic fallback through WinRM/WinRS/DCOM.
- Searchable, scrollable, selectable, copyable and exportable Fleet and Agent logs with complete STDOUT, STDERR, exit codes and stack traces.

See the [Fleet management documentation](https://github.com/swayze-sys/Winget-Studio-Source/blob/fleet-management/Documentation/Fleet-Management.en.md). This branch is not part of the public 2.08.5 binaries yet.

## Requirements

- Windows 10 build 19041 or later; Windows 11 is recommended.
- x64 system with WinGet / Microsoft App Installer.
- .NET 10 Desktop Runtime and Windows App SDK Runtime as required by the installer.
- Optional provider tools (Chocolatey, Node.js/npm, Python/pip, .NET SDK or PowerShellGet) for their respective catalogs.

## Installation

Download the public setup from [GitHub Releases](https://github.com/swayze-sys/Winget-Studio/releases/latest). The offline bundle contains the payload and can be extracted before running WingetStudio-Setup.exe; the web setup downloads and verifies the same payload. The installer performs SHA-256 validation and preserves user data during updates.

## Updates

The public 2.08.5 application checks its configured GitHub release channel and applies confirmed updates through the existing installer. The updater never replaces individual application files.

## Privacy and local data

Winget Studio stores settings, icon cache and update history locally. It sends no telemetry.

## Release history

See [CHANGELOG.md](CHANGELOG.md) for the complete public release history and the Fleet development entry.

Winget Studio is authored and maintained by **Sven Philipp**.
