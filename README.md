Author and developer: Sven Philipp
Current application version: 2.01

A local WinUI 3 application for clearly managing installed WinGet packages.

Features
Large application cards with extracted icons
Installed and available version for each application
Last update time from the registry and the application's own update history
Search and multi-selection for targeted updates
Direct single-package updates by clicking the update status, plus sorting by name, available updates, or last update time
Combinable filters for hiding up-to-date applications or available updates
Quick action to select all available updates
Persistent update history with old/new version, duration, result, and exit code
Export and import of WinGet-compatible application lists for Windows reinstallation
Separate export/import selection dialogs with search, small icons, and “Select all” / “Select none”
Detail view with publisher, installation path, package ID, source, and version information
Modern black WinUI title bar with a custom app icon and transparent desktop acrylic background
Highly transparent Thin Acrylic background with low tint and luminosity opacity, plus glass-style card, title, and status surfaces
Status displayed directly on the application card: up to date, available, running, successful, or failed
Separate Debug tab with complete commands, process IDs, stdout, stderr, and exit codes
Secure package ID passing via ProcessStartInfo.ArgumentList
Dedicated Settings window for update behavior, sources, pins, import/export, network, installers, and diagnostics
Source allowlist plus adding, updating, removing, and resetting WinGet repositories
Management of normal, blocking, and version-bound WinGet pins
Detailed risk explanations as hover information for every setting
Mandatory per-application confirmation when using --force or --uninstall-previous
Switchable large-icon and compact list views with the selected view saved persistently
Freely configurable list columns for package ID, source, versions, publisher, update time, and status
Persistent status bar showing the current operation, package progress, and summarized result
“Discover Apps” repository catalog with search, source information, installed-state indicator, and direct installation
Additional providers for npm, Chocolatey, Pip/PyPI, global .NET Tools, and PowerShell Gallery
Provider filtering and, where supported by the catalog, sorting by popularity or downloads
Dedicated “Manage Programs” tab with search, details, confirmed uninstallation, and manufacturer-provided modify/repair functionality
Live display of the most recently emitted WinGet output line directly below the progress bar
Automatically hiding status area: five seconds after the last activity, the workspace is freed up again
Clickable column headers with ascending and descending sorting in application, catalog, management, and history lists
Compact tab bar displaying application and update counts; the large page heading has been removed
Context-sensitive update advisory when clicking “Retry”, including an error explanation, recommendation, and directly executable repair options
Controlled reinstallation when the installation technology has changed: confirm the registered manufacturer uninstaller, verify removal through the registry and WinGet, and only then reinstall the same package
Local version detection for versions reported as unknown by WinGet using the matching main executable (ProductVersion, falling back to FileVersion), with a visible indication of the version source
About dialog showing the author, current version, and a version history derived from the development milestones
Cancel button in the status bar that terminates active WinGet and provider process trees and prevents any additional packages from being started
Detection of running processes from the installation directory, with a normal close dialog and safe skipping of background processes that could not be closed
Restart continuation using a local status file and Windows RunOnce; remaining selected packages are resumed after the next sign-in
Optional automatic updates through Windows Task Scheduler instead of a permanently running service; unattended runs do not use risky switches and skip running applications
Confirmed fallback to Chocolatey, npm, Pip, .NET Tool, or PowerShell Gallery after a WinGet failure, including package ID, version, and source information
Authenticode verification of local main executable files, including signature status, publisher, and verified file path
Windows app notification after scheduled runs showing the total number of packages, successful updates, failures, skipped packages, packages pending a restart, compact application names, and error messages, with direct navigation to the update history
Portable Windows toast fallback with its own App ID, Start menu shortcut, and wingetstudio://history activation for self-contained installations without the Windows App SDK Singleton package
Runtime diagnostics for Framework, Main, Singleton, and DDLM, plus signature-verified installation/repair of the official Microsoft Windows App SDK Runtime 1.8.10 with automatic re-registration and test notification
Separate WingetStudio.NotificationHost running with standard user privileges and launched through a least-privilege scheduled task; updates remain elevated while Windows app notifications are sent from the Microsoft-supported non-elevated context
One-time retries using --include-unknown, --include-pinned, --interactive, --uninstall-previous, or --force without unintentionally changing the global settings
Direct display of detected WinGet/manufacturer installation logs in the advisory dialog
Selectable and copyable text in all columns of the process and error logs
Detection of common WinGet errors such as unknown versions, installer failures, installation technology changes, non-applicable updates, locked files, concurrent installations, pins, network issues, and storage problems
Requirements
Windows 10 build 19041 or later, or Windows 11
.NET 10 SDK for building
WinGet (Microsoft App Installer) for detecting and updating applications
Windows App SDK Runtime 1.8.10 is recommended for modern system notifications; it can be checked in the settings and installed or repaired after validating the Microsoft signature. Without it, the portable toast fallback remains active.
For the additional catalogs, the respective package manager must be installed locally: Node.js/npm, Chocolatey, Python/pip, .NET SDK, or PowerShellGet. Missing providers are skipped and indicated in the user interface.
Build and Run
dotnet restore
dotnet build -c Release
dotnet run -c Release
Modern Installer

The Installer directory contains a custom dark setup bootstrapper with a large logo panel, component checks, download progress, SHA-256 payload verification, Microsoft signature verification, and Windows uninstallation support. The directly distributable installer is generated with the following command:

.\Installer\Build-Installer.ps1

The setup installs required components such as WinGet and .NET Runtime 10 only when needed. Windows App SDK Runtime 1.8.10 is preselected as the recommended notification component, while Chocolatey, Node.js/npm, Python/pip, .NET SDK/Tools, and PowerShell 7 deliberately remain optional. For a small web installer, Publish-OnlineInstaller.ps1 generates a signable manifest containing the download URL, size, and SHA-256 hash of the application package.

The project uses the Windows App SDK Runtime in self-contained mode. Winget Studio runs in the user context by default so that per-user installations remain visible. Individual updates and installations can be elevated once via UAC when required; alternatively, launching as administrator can be enabled in the settings. Risky switches require confirmation for every package regardless of the saved setting.

Local Data

The icon cache, settings, and update history are stored under %LOCALAPPDATA%\WingetStudio. Winget Studio itself does not send any telemetry data. Global WinGet settings and values managed through Group Policy are not overwritten without explicit user action.

The additional providers are independent package managers and are not native winget source entries. For Pip, the official CLI no longer supports general free-text search; instead, the entered package name is queried directly against PyPI. “Modify” is only available if the application has registered a ModifyPath in Windows.
