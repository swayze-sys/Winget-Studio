# Winget Studio

Autor und Entwickler: **Sven Philipp**  
Aktuelle Anwendungsversion: **2.07**

Eine lokale WinUI-3-Anwendung zur übersichtlichen Verwaltung installierter WinGet-Pakete.

## Funktionen

- Große Programmkarten mit extrahierten Icons
- Installierte und verfügbare Version pro Anwendung
- Zeitpunkt des letzten Updates aus Registry und eigener Update-Historie
- Suche und Mehrfachauswahl für gezielte Updates
- Direktes Einzelupdate per Klick auf den Update-Status sowie Sortierung nach Name, verfügbaren Updates oder letztem Updatezeitpunkt
- Kombinierbare Filter zum Ausblenden aktueller Programme oder verfügbarer Updates
- Schnellaktion zum Auswählen aller verfügbaren Updates
- Dauerhafter Updateverlauf mit alter/neuer Version, Dauer, Ergebnis und Exit-Code
- Export und Import WinGet-kompatibler Programmlisten für eine Windows-Neuinstallation
- Separate Export-/Import-Auswahlfenster mit Suche, kleinen Icons sowie „Alle auswählen“ und „Keine auswählen“
- Detailansicht mit Herausgeber, Installationspfad, Paket-ID, Quelle und Versionsinformationen
- Moderne schwarze WinUI-Titelleiste mit eigenem App-Icon und transparentem Desktop-Acrylhintergrund
- Stark transparenter Thin-Acrylic-Hintergrund mit niedriger Tönungs- und Luminositätsabdeckung sowie gläsernen Karten-, Titel- und Statusflächen
- Status direkt auf der Programmkarte: aktuell, verfügbar, läuft, erfolgreich oder fehlgeschlagen
- Separates Debug-Tab mit vollständigen Befehlen, Prozess-IDs, stdout, stderr und Exit-Codes
- Sichere Übergabe der Paket-ID über `ProcessStartInfo.ArgumentList`
- Eigenes Settings-Fenster für Updateverhalten, Quellen, Pins, Import/Export, Netzwerk, Installer und Diagnose
- Quellen-Freigabeliste sowie Hinzufügen, Aktualisieren, Entfernen und Zurücksetzen von WinGet-Repositories
- Verwaltung normaler, blockierender und versionsgebundener WinGet-Pins
- Ausführliche Risikoerklärungen als Hover-Info an jeder Einstellung
- Zwingende Einzelbestätigung pro Programm bei `--force` oder `--uninstall-previous`
- Umschaltbare große Symbol- und kompakte Listenansicht mit gespeicherter Auswahl
- Frei ein- und ausblendbare Listenspalten für Paket-ID, Quelle, Versionen, Herausgeber, Updatezeitpunkt und Status
- Permanente Statusleiste mit aktuellem Arbeitsschritt, Paketfortschritt und zusammengefasstem Ergebnis
- Repository-Katalog „Apps entdecken“ mit Suche, Quellenangabe, installierter Kennzeichnung und Direktinstallation
- Zusätzliche Provider für npm, Chocolatey, Pip/PyPI, globale .NET Tools und PowerShell Gallery
- Parallele freie Suche über WinGet und alle verfügbaren Zusatzprovider; Katalogsuche und Installationsstatus werden je Provider ebenfalls gleichzeitig abgefragt
- Schokoladentafel als eindeutiges Chocolatey-Symbol in der Provider-Spalte
- Kollisionsfreie App-Updates durch einen eigenen temporären Ordner pro Setup-Download
- Frei wählbare Provider mit Live-Status, Trefferzahl und Laufzeit pro paralleler Suche
- Erweiterte Discover-Paketdetails mit Projekt-, Lizenz-, Installer- und Vertrauensinformationen
- Update-Vorschau für Versionswechsel, Quellen, Herausgeber, laufende Prozesse und Installeroptionen
- Keine erneute Sprachabfrage des Installers im App-Update-Modus
- Providerfilter und – soweit vom Katalog geliefert – Sortierung nach Popularität oder Downloads
- Eigenes Tab „Programme verwalten“ mit Suche, Details, bestätigter Deinstallation und Herstellerfunktion zum Ändern/Reparieren
- Live-Anzeige der zuletzt ausgegebenen WinGet-Zeile direkt unter dem Fortschrittsbalken
- Automatisch ausblendende Statuszeile: fünf Sekunden nach der letzten Aktivität wird der Arbeitsbereich wieder freigegeben
- Klickbare Spaltenköpfe mit auf- und absteigender Sortierung in Programm-, Katalog-, Verwaltungs- und Verlaufslisten
- Kompakte Tabzeile mit Programm- und Updateanzahl; die große Seitenüberschrift entfällt
- Kontextabhängiges Update-Advisory beim Klick auf „Erneut versuchen“ mit Fehlererklärung, Empfehlung und direkt ausführbaren Reparaturoptionen
- Kontrollierte Neuinstallation bei gewechselter Installationstechnologie: registrierten Hersteller-Uninstaller bestätigen, die Entfernung über Registry und WinGet verifizieren und erst danach dasselbe Paket erneut installieren
- Lokale Versionsbestimmung bei von WinGet als unbekannt gemeldeten Versionen über die passende Haupt-EXE (`ProductVersion`, ersatzweise `FileVersion`) mit sichtbarer Quellenkennzeichnung
- Info-Dialog mit Autor, aktueller Version und aus den Entwicklungsschritten aufgebauter Versionshistorie
- Abbruchschaltfläche in der Statusleiste, die aktive WinGet- und Provider-Prozessbäume beendet und keine weiteren Pakete startet
- Erkennung laufender Prozesse aus dem Installationsordner mit normalem Schließen-Dialog und sicherem Überspringen nicht geschlossener Hintergrundprozesse
- Neustart-Fortsetzung über eine lokale Statusdatei und Windows `RunOnce`; verbleibende ausgewählte Pakete werden nach der nächsten Anmeldung weitergeführt
- Optionale automatische Updates über die Windows-Aufgabenplanung statt eines permanenten Dienstes; unbeaufsichtigte Läufe verwenden keine riskanten Schalter und überspringen laufende Programme
- Bestätigter Wechsel zu Chocolatey, npm, Pip, .NET Tool oder PowerShell Gallery nach einem WinGet-Fehler, einschließlich Paket-ID-, Versions- und Quellenanzeige
- Authenticode-Prüfung lokaler Haupt-EXE-Dateien mit Signaturstatus, Herausgeber und geprüftem Dateipfad
- Windows-App-Benachrichtigung nach geplanten Läufen mit Gesamtzahl, Erfolgen, Fehlern, übersprungenen und nach Neustart ausstehenden Paketen, kompakten Programmnamen und Fehlermeldungen sowie direktem Sprung in den Updateverlauf
- Portabler Windows-Toast-Fallback mit eigener App-ID, Startmenü-Verknüpfung und `wingetstudio://history`-Aktivierung für selbstenthaltende Installationen ohne Windows-App-SDK-Singleton-Paket
- Runtime-Diagnose für Framework, Main, Singleton und DDLM sowie signaturgeprüfte Installation/Reparatur der offiziellen Microsoft Windows App SDK Runtime 1.8.10 mit automatischer Neuregistrierung und Testbenachrichtigung
- Separater `WingetStudio.NotificationHost` mit normalen Benutzerrechten, gestartet über eine Least-Privilege-Aufgabe; dadurch bleiben Updates erhöht, während Windows-App-Benachrichtigungen im von Microsoft unterstützten, nicht erhöhten Kontext versendet werden
- Einmalige Wiederholungen mit `--include-unknown`, `--include-pinned`, `--interactive`, `--uninstall-previous` oder `--force`, ohne die globalen Einstellungen unbeabsichtigt zu verändern
- Direkte Anzeige erkannter WinGet-/Hersteller-Installationsprotokolle im Advisory-Dialog
- Markier- und kopierbarer Text in allen Spalten des Prozess- und Fehlerprotokolls
- Erkennung häufiger Winget-Fehler wie unbekannter Version, Installerfehler, Technologiewechsel, nicht anwendbarem Update, gesperrten Dateien, paralleler Installation, Pins, Netzwerk- und Speicherproblemen

- Kompakte Provider-Auswahl mit Checkboxen, robuste PowerShell-Gallery-Suche sowie Provider-Status und Laufzeit.
- Updateverlauf mit Mehrfachauswahl, vollständigem Kopieren und CSV-Export.
- Gespeicherte Update-Aussetzungen können in den Einstellungen eingesehen und gelöscht werden.

## Voraussetzungen

- Windows 10 ab Build 19041 oder Windows 11
- .NET 10 SDK zum Bauen
- WinGet (Microsoft App Installer) zum Einlesen und Aktualisieren von Programmen
- Die Windows App SDK Runtime 1.8.10 ist für moderne Systembenachrichtigungen empfohlen; sie kann in den Einstellungen geprüft und nach gültiger Microsoft-Signatur installiert oder repariert werden. Ohne sie bleibt der portable Toast-Fallback aktiv.
- Für die zusätzlichen Kataloge muss der jeweilige Paketmanager lokal vorhanden sein: Node.js/npm, Chocolatey, Python/pip, .NET SDK oder PowerShellGet. Fehlende Provider werden übersprungen und in der Oberfläche ausgewiesen.

## Bauen und starten

```powershell
dotnet restore
dotnet build -c Release
dotnet run -c Release
```

## Moderner Installer

Unter `Installer` liegt ein eigener dunkler Setup-Bootstrapper mit großer Logo-Seitenfläche, Komponentenprüfung, Downloadfortschritt, SHA-256-Payloadprüfung, Microsoft-Signaturprüfung und Windows-Deinstallation. Das direkt verteilbare Ergebnis wird mit folgendem Befehl erzeugt:

```powershell
.\Installer\Build-Installer.ps1
```

Das Setup installiert erforderliche Komponenten wie WinGet und .NET Runtime 10 nur bei Bedarf. Windows App SDK Runtime 1.8.10 ist als empfohlene Benachrichtigungskomponente vorausgewählt; Chocolatey, Node.js/npm, Python/pip, .NET SDK/Tools und PowerShell 7 bleiben bewusst optional. Für einen kleinen Web-Installer erzeugt `Publish-OnlineInstaller.ps1` ein signierbares Manifest mit Downloadadresse, Größe und SHA-256-Hash des Programmpakets.

Das Projekt verwendet die Windows App SDK Runtime selbstenthaltend. Winget Studio startet standardmäßig im Benutzerkontext, damit benutzerbezogene Installationen sichtbar bleiben. Einzelne Updates und Installationen können bei Bedarf einmalig über UAC erhöht werden; alternativ lässt sich der Start als Administrator in den Einstellungen aktivieren. Riskante Schalter werden unabhängig von der gespeicherten Einstellung vor jedem Paket nochmals bestätigt.

## Lokale Daten

Icon-Cache, Einstellungen und Updateverlauf liegen unter `%LOCALAPPDATA%\WingetStudio`. Winget Studio selbst sendet keine Telemetriedaten. Globale WinGet-Einstellungen und durch Gruppenrichtlinien verwaltete Werte werden nicht ungefragt überschrieben.

Die zusätzlichen Provider sind eigenständige Paketmanager und keine nativen `winget source`-Einträge. Bei Pip unterstützt die offizielle CLI keine allgemeine Freitextsuche mehr; dort wird der eingegebene Paketname gezielt bei PyPI abgefragt. „Ändern“ ist nur verfügbar, wenn das Programm einen `ModifyPath` in Windows registriert hat.
