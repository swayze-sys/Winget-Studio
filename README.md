# Winget Studio

Winget Studio is a modern WinUI 3 desktop application for discovering, monitoring and maintaining Windows applications through WinGet and additional package providers.

## Highlights

- **Installed applications and updates** – view installed versions, available versions, sources and update state in a responsive icon grid or sortable list.
- **Safe update workflow** – select one or many applications, review progress and live WinGet output, and use the Update Advisor for unknown versions, installer technology changes, running processes and other failures.
- **App discovery** – browse curated categories such as browsers, communication, developer tools, games, Microsoft tools, multimedia, professional tools and utilities; install packages directly from the catalog.
- **Multiple providers** – use WinGet together with supported Chocolatey, npm, pip, .NET tool and PowerShell Gallery sources where applicable.
- **User and administrator contexts** – keep the main UI in the user context while an authenticated Admin Helper performs operations that require elevation. User-scoped installations remain visible.
- **History, diagnostics and notifications** – inspect complete command, process, stdout/stderr and exit-code logs; keep an update history and receive grouped Windows notifications for successful and failed operations.
- **Import and export** – select applications and the state to transfer, then create or restore a portable package list.
- **Controls and automation** – configure sources, update rules/pins, filters, scheduled update runs, language, appearance, network behavior and diagnostic retention.
- **Installer and self-update** – use the online or offline installer. The application can check the GitHub release channel, verify the downloaded installer and update itself through the existing setup bootstrapper.

## Requirements

- Windows 10 version 19041 or later (Windows 11 recommended)
- x64 system
- .NET 10 Desktop Runtime and Windows App SDK Runtime (the installer can install required components)
- WinGet / App Installer for package operations

## Installation

Use `WingetStudio-WebSetup.exe` for the small online installer. Use `WingetStudio-Setup.exe` or `WingetStudio-Setup-2.01.zip` when the complete offline bundle is preferred. The installer supports a language selection, optional components, integrity checks and a repairable installation path.

## Updates

The installed application reads `update-channel.json` next to `WingetStudio.exe`. The release channel points to the public GitHub latest-release API for this project and selects the first HTTPS `.exe` asset whose name contains `Setup`. Updates are always confirmed by the user and are installed through the signed/verified setup flow rather than replacing individual application files.

## Project

Winget Studio is authored and maintained by **Sven Philipp**. See the German README, `CHANGELOG.md` and the `Documentation` folder for implementation and release details.

License information is provided in the repository's license file.
