# Winget Studio

Winget Studio is a modern WinUI 3 desktop application for discovering, monitoring, installing, updating, and diagnosing Windows applications through WinGet and supported additional package providers.

**Current release:** 2.03 · [Release notes](https://github.com/swayze-sys/Winget-Studio/releases/tag/v2.03) · [Deutsch](README.de.md)

## Highlights

- Review installed and available versions in an icon grid or sortable list.
- Select one or many updates and follow live WinGet output and progress.
- Use the Update Advisor for unknown versions, installer technology changes, running processes, pins, network issues, and other common failures.
- Discover and install applications from curated categories.
- Search WinGet and all available supported Chocolatey, npm, pip, .NET Tool, and PowerShell Gallery providers concurrently.
- Keep the main interface in the user context while an authenticated helper performs operations that require elevation.
- Inspect command, process, stdout/stderr, exit-code, update-history, and diagnostic information.
- Import and export portable application lists.
- Configure sources, pins, filters, scheduled update runs, language, appearance, network behavior, and diagnostic retention.
- Receive grouped Windows notifications for completed scheduled runs.
- Check the GitHub release channel and install a confirmed Winget Studio update through the existing setup workflow.

## Requirements

- Windows 10 version 19041 or later; Windows 11 is recommended.
- x64 system.
- WinGet / Microsoft App Installer for WinGet package operations.
- .NET 10 Desktop Runtime and Windows App SDK Runtime. The installer can install required components when needed.
- The corresponding package manager for optional Chocolatey, npm, pip, .NET Tool, or PowerShell Gallery integration.

## Installation

Download the current release from [GitHub Releases](https://github.com/swayze-sys/Winget-Studio/releases/latest).

- [WingetStudio-WebSetup.exe](https://github.com/swayze-sys/Winget-Studio/releases/download/v2.03/WingetStudio-WebSetup.exe) is the small online installer. Its embedded manifest uses the public `v2.03` release URLs and verifies the downloaded payload with SHA-256.
- [WingetStudio-Setup-2.03.zip](https://github.com/swayze-sys/Winget-Studio/releases/download/v2.03/WingetStudio-Setup-2.03.zip) is the complete offline bundle. Extract it fully and run `WingetStudio-Setup.exe` from the extracted directory.

The installer supports component checks, SHA-256 payload verification, optional dependencies, Windows uninstallation, and repair/update operation through the registered installation path.

## Updates

The installed application reads `update-channel.json` next to `WingetStudio.exe`. Version 2.03 uses the public latest-release endpoint:

`https://api.github.com/repos/swayze-sys/Winget-Studio/releases/latest`

The updater accepts HTTPS release assets whose filename contains `Setup` and ends in `.exe`. It asks for confirmation, downloads the selected setup executable, verifies it, and invokes the installer with the update flow instead of replacing individual application files.

### One-time update path for installed 2.01 builds

The original 2.01 updater does not normalize tags written as `v.2.02` correctly and can keep a downloaded setup file locked while validating a GitHub-provided digest. Version 2.03 fixes those defects and also isolates concurrent downloads in unique temporary directories. To update once from 2.01, close every Winget Studio window and start exactly one instance from PowerShell with the process-only compatibility feed:

```powershell
$env:WINGET_STUDIO_UPDATE_FEED='https://raw.githubusercontent.com/swayze-sys/Winget-Studio/main/update-compat-v2.01-to-v2.03.json'
& 'C:\Program Files\Winget Studio\WingetStudio.exe'
```

Wait for the automatic update prompt, or use **Settings → Updates → Check now** once. Do not start both paths at the same time. The environment override exists only for that PowerShell process tree; normal 2.03 starts use the regular GitHub latest-release channel again.

## Privacy and local data

Winget Studio stores its icon cache, settings, update history, and related local state under `%LOCALAPPDATA%\WingetStudio`. The application itself does not send telemetry. Global WinGet settings and Group Policy-managed values are not overwritten without an explicit user action.

## Release history

See [CHANGELOG.md](CHANGELOG.md) for the current release changes and earlier milestones.

Winget Studio is authored and maintained by **Sven Philipp**.
