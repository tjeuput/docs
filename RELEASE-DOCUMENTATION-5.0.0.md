# infoskop-Base 5.0.0 - Complete Release Documentation

**Release Date**: September 2025
**Version**: 5.0.0
**Status**: Production Release

---

## Table of Contents

1. [Overview](#overview)
2. [infoskop-Base.exe](#infoskop-baseexe)
3. [infoskop-Monitor](#infoskop-monitor)
4. [infoskop::LEA (NEW)](#infoskoplea-new)
5. [Signexport.exe](#signexportexe)
6. [MediaServerStarter](#mediaserverstarter)
7. [VDDS-stage1.exe](#vdds-stage1exe)
8. [Starter.exe](#starterexe)
9. [HL7-Server](#hl7-server)
10. [Infoskop-Client.exe](#infoskop-clientexe)
11. [Updater & Full-Setup](#updater--full-setup)
12. [Testing Documentation](#testing-documentation)
13. [Migration Guide](#migration-guide)

---

## Overview

Version 5.0.0 ist ein Major Release mit signifikanten Verbesserungen über alle Komponenten hinweg:

### Highlights
- 🆕 **infoskop::LEA** - Neues Produkt für Leistungsabrechnung
- 🔄 **Automatische Überwachung** - Starter.exe überwacht und repariert automatisch
- 🛡️ **Verbesserte Dienstverwaltung** - Unterstützung für Mehrfach-Installationen
- 📧 **E-Mail-Zuverlässigkeit** - Korrekte SMTP-Validierung und Status-Rückmeldung
- 🎨 **UX-Verbesserungen** - Ladeanzeigen, Icons, Splash-Screen-Optimierung
- 🔧 **Onlinefunktions-Kontrolle** - Konsistente Deaktivierung über alle Komponenten
- 💻 **64-Bit Focus** - Nur noch 64-Bit und ARM64 Architekturen

### Breaking Changes
- ❌ **32-Bit Support entfernt** - Nur noch 64-Bit-Systeme werden unterstützt
- ⚠️ **Bonjour 32-Bit entfernt** - Zwei neue 64-Bit-Installer (Intel/ARM)

---

## infoskop-Base.exe

### Fehlerbehebungen

#### E-Mail-Versandstatus - SMTP-Validierung
**Ticket**: [INFO-1243](./details/info-1243.md) | [QS-227](./details/qs-227.md)

Behebung eines kritischen Fehlers, wodurch E-Mails scheinbar erfolgreich versendet werden konnten, obwohl fehlerhafte Daten für den SMTP-Server hinterlegt waren.

**Auswirkung**:
- ✅ Korrekte Validierung der SMTP-Serverdaten
- ✅ Authentifizierungsfehler werden erkannt und gemeldet
- ✅ Tatsächlicher Versandstatus wird zurückgemeldet
- ✅ Verhindert falsche Erwartungen bei Benutzern

**Details**: [Vollständige Dokumentation →](./details/info-1243.md)

---

## infoskop-Monitor

### Neue Funktionen

#### 1. Flexible Bildgrößenanpassung
Anwender können nun die Größe eingebetteter Bilder in E-Mail- und Vorlagentexten flexibel anpassen.

**Features**:
- Drag & Drop von Bildern im WYSIWYG-Editor (CK5)
- Größenanpassung direkt im Editor
- Bessere Gestaltungsmöglichkeiten für E-Mails und Vorlagen

**Bereich**: WYSIWYG-Editor | Mail-/Vorlagentexte

---

### Fehlerbehebungen

#### 2. Link-Handling im Editor
**Ticket**: [QS-177](./details/qs-177.md)

Ein Problem wurde behoben, das das Öffnen von Links in E-Mail- und Vorlagentexten sowie im Formularlinkbaukasten im lokalen Browser verhinderte.

**Fixes**:
- ✅ Links öffnen korrekt im lokalen Browser
- ✅ Formularlinkbaukasten: Links müssen direkt angeklickt werden für Vorschau
- ✅ Verhindert unbeabsichtigtes Öffnen

**Details**: [Vollständige Dokumentation →](./details/qs-177.md)

---

#### 3. Preisübernahme mit Euro-Zeichen
**Ticket**: [QS-97](./details/qs-97.md)

Die Preisübernahme im PA- und Bleaching-Cockpit funktioniert nun auch korrekt, wenn der Preis ein Euro-Zeichen (€) enthält.

**Betroffene Bereiche**:
- PA-Cockpit
- Bleaching-Cockpit

**Details**: [Vollständige Dokumentation →](./details/qs-97.md)

---

#### 4. infoskop::ORA-Lizenz
**Ticket**: [INFO-1194](./details/info-1194.md)

Es wurde ein Fehler bei der Abfrage der infoskop::ORA-Lizenz behoben.

**Auswirkung**:
- ✅ ::ORA-Kunden können lizenzierte Funktionen nutzen
- ✅ Antwortfunktion wird korrekt freigeschaltet
- ✅ Konsistente Lizenzprüfung

**Details**: [Vollständige Dokumentation →](./details/info-1194.md)

---

### Anpassungen

#### 5. Cockpit Icons aktualisiert
**Ticket**: [QS-222](./details/qs-222.md)

Fehlende Icons in den Cockpits wurden ergänzt und aktualisiert.

**Verbesserungen**:
- Modernisiertes Icon-Design
- Konsistente Darstellung
- Bessere Erkennbarkeit von Funktionen

**Details**: [Vollständige Dokumentation →](./details/qs-222.md)

---

#### 6. Offline-Anzeigen optimiert
**Tickets**: [QS-187](./details/qs-187.md) | [AZUBI-403](./details/azubi-403.md) | [AZUBI-421](./details/azubi-421.md)

Die Anzeigen bei deaktivierter Onlinefunktion wurden umfassend überarbeitet.

**Verbesserungen**:
- ✅ Onlineformular-Einstellungen werden korrekt ausgeblendet
- ✅ E-Mail-Versand wird systemweit blockiert bei Deaktivierung
- ✅ Konsistentes Verhalten in infoskop-Base, Monitor und App
- ✅ Klare Benutzerführung

**Related Testing**: [IT-277 Test Case](./details/it-277.md)

**Details**:
- [QS-187 - Offline-Anzeigen](./details/qs-187.md)
- [AZUBI-403 - Zugriff auf Onlineformular-Einstellungen](./details/azubi-403.md)
- [AZUBI-421 - E-Mail-Versand bei deaktivierter Funktion](./details/azubi-421.md)

---

#### 7. Antwortfunktion
Die Antwortfunktion ist nur für ::ORA-Kunden aktiv. Für andere Nutzer wurde die Anzeige angepasst und die Funktion deaktiviert.

**Lizenzbasierte Freischaltung**:
- Nur ::ORA-Lizenz: Funktion aktiv
- Ohne ::ORA-Lizenz: Funktion deaktiviert und ausgeblendet

---

### Optimierungen

#### 8. Gesamtbearbeitung Warnungseinstellungen
**Ticket**: [AZUBI-399](./details/azubi-399.md)

Das Anzeigeverhalten der Gesamtbearbeitung in den Warnungseinstellungen wurde verbessert.

**Fixes**:
- ✅ Konsistente Anzeige beim Umschalten zwischen Tabs
- ✅ Korrekte Synchronisation bei "Alles Ja/Nein"-Option
- ✅ Keine inkonsistenten Anzeigezustände mehr

**Details**: [Vollständige Dokumentation →](./details/azubi-399.md)

---

#### 9. Patientendaten-Löschung optimiert
**Ticket**: AZUBI-401

Der Ablauf der Löschung von Patientendaten im Monitor wurde angepasst und optimiert.

**Verbesserungen**:
- Schnellerer Löschvorgang
- Bessere Rückmeldung an Benutzer
- Korrekte Validierung vor Löschung

---

## infoskop::LEA (NEW)

🆕 **Neues Produkt ab Version 5.0.0**

### Einbindung und Funktionen

#### 1. Webframe für Client
Einbindung des neuen Webframes für den Client

**Features**:
- Eigenständige Windows-Fensterinstanz
- Integration in infoskop-Client.exe
- Moderne Web-basierte Oberfläche

---

#### 2. Base-Verwaltung
Funktionen in der Base zur Verwaltung der Anfragen und Datenhaltung

**Funktionalität**:
- Anfragenverwaltung
- Datenpersistenz
- API für Client-Kommunikation

---

#### 3. Automatische Lizenzierung
Automatische Aktivierung der Lizenz bei korrekt hinterlegtem Leistungskatalog

**Lizenzmodell**:
- Automatische Erkennung der ::LEA-Lizenz
- Aktivierung ohne manuellen Eingriff
- Abhängig von Leistungskatalog-Konfiguration

---

## Signexport.exe

### Optimierungen

#### 1. Proxy-Konfiguration
Option hinzugefügt, um einen Proxy zu konfigurieren.

**Anwendungsfall**:
- Firmen-Netzwerke mit Proxy-Servern
- Konfigurierbare Proxy-Einstellungen
- Unterstützung für authentifizierte Proxys

---

## MediaServerStarter

### Optimierungen

#### 1. Dienst-Installation korrigiert
**Ticket**: [INFO-1157](./details/info-1157.md)

Die Installation des MediaServerStarter als Dienst wurde verbessert. Ein schwerwiegender Fehler, der zu unleserlichen Dienstnamen unter Windows führte, wurde behoben.

**Fixes**:
- ✅ Dienstnamen sind korrekt lesbar
- ✅ Windows Service Manager kann Dienst verwalten
- ✅ Unterstützung für Mehrfach-Installationen

**Details**: [Vollständige Dokumentation →](./details/info-1157.md)

---

#### 2. Dienstverwaltung
Der MediaServerStarter speichert Dienstnamen in der Base-Config, um Mehrfachinstallationen klar zuzuordnen.

**Konfigurationsparameter**:
```ini
[Server]
mname = Name des Dienstes vom MediaServer
```

**Vorteile**:
- Eindeutige Identifikation bei mehreren MediaServern
- Korrekte Verwaltung durch Updater
- Spätere Versionen können Dienst identifizieren

---

## VDDS-stage1.exe

### Fehlerbehebungen

#### 1. Evident-Konfiguration
**Tickets**: [INFO-1190](./details/info-1190.md) | [QS-218](./details/qs-218.md)

Behebung eines Fehlers, welcher die automatische Evident Konfiguration nicht richtig erkannt hat.

**Fixes**:
- ✅ Automatische Konfigurationserkennung funktioniert
- ✅ Evident-Parameter werden korrekt ausgelesen
- ✅ Datenabgleich mit Evident läuft zuverlässig
- ✅ Reduzierter Konfigurationsaufwand

**Details**: [Vollständige Dokumentation →](./details/info-1190.md)

---

## Starter.exe

### Neue Funktionen

#### 1. Automatische Selbstüberwachung
**Ticket**: [INFO-1187](./details/info-1187.md)

Der Starter.exe überwacht nun automatisch die Funktionalität des TCP-Socketserver der infoskop-Base.exe und startet die Anwendung bei Problemen neu.

**Features**:
- ✅ **Default: AN** - Standardmäßig aktiviert
- ✅ **Adaptive Timeouts** - Erhöhen sich bei wiederholten Neustarts
- ✅ **Intelligente Logik** - Ermöglicht langwierigen Aktionen Erfolg
- ✅ **Erweiterte Protokollierung** - report.dat + Logcheck-Integration

**Konfiguration** (Base-config):
```ini
[server]
restartWhenUnresponsive = 1          # 1=AN, 0=AUS
lifesignToBaseInterval = 5000         # Prüfintervall (ms)
lifesignRestartBusyBaseAfterInterval = 30000  # Timeout vor Neustart (ms, erhöht sich automatisch)
```

**Details**: [Vollständige Dokumentation →](./details/info-1187.md)

---

### Optimierungen

#### 2. Dienstverwaltung
Der Starter speichert Dienstnamen in der Base-Config, um Mehrfachinstallationen eindeutig zuordnen zu können.

**Konfigurationsparameter**:
```ini
[Server]
bname = Name des Dienstes der infoskop-Base
mname = Name des Dienstes vom MediaServer
```

---

#### 3. Fehlerprotokollierung
Der Starter protokolliert im Fehlerfall seine Versuche in `report.dat`, die Base zu erreichen.

**Features**:
- Detaillierte Verbindungsprotokolle
- Automatische Logcheck-Integration
- Bessere Diagnose bei Problemen

---

#### 4. HL7-Server-Überwachung
HL7-Server werden nun automatisch überwacht. Beim Beenden des Base-Starters schließt der HL7-Server seinen Dienst „sanft", wodurch Netzwerkprobleme und lange Timeouts vermieden werden.

**Konfiguration** (Base-config):
```ini
[hl7]
smartHandling = 0          # 1=AN (benötigt hl7/enabled=1)
waitforclose = 6000        # Wartezeit für sanftes Beenden (ms)
```

**Vorteile**:
- Keine Netzwerk-Timeouts mehr
- Ordnungsgemäßes Schließen des Socket-Servers
- Vermeidung von Port-Blockierungen

**Siehe auch**: [HL7-Server - Sanftes Schließen](#hl7-server)

---

#### 5. Dienst-Installation korrigiert
**Ticket**: [INFO-1156](./details/info-1156.md)

Optimierungen für die Installation als Dienst, behebt einen Fehler, bei dem installierte Dienstnamen korrupt und nicht für Windows leserlich waren.

**Details**: [Vollständige Dokumentation →](./details/info-1156.md)

---

## HL7-Server

### Optimierungen

#### 1. Socket-Server - Sanftes Schließen
Ermöglicht nun sanftes Schließen des Socket-Servers (in Verbindung mit Starter.exe).

**Konfiguration** (HL7-Server config):
```ini
[server]
useChilkatSockets = 0  # 1=AN (Voraussetzung für sanftes Schließen)
                       # Wird automatisch aktiviert, wenn module/orbis=1 und server/openstream=1
```

**Technische Details**:
- Wechsel von alten Sockets auf neuere Chilkat-Sockets
- Mehr Möglichkeiten und Kontrolle
- Sauberes Schließen ohne Netzwerk-Timeouts

**Voraussetzung**: `server/useChilkatSockets=1` muss aktiviert sein

---

## Infoskop-Client.exe

### Neue Funktionen

#### 1. ::LEA-Unterstützung
Unterstützung für das neue Produkt infoskop::LEA implementiert.

**Features**:
- Aufruf der Windows-Applikation als eigenständige Fensterinstanz
- Abfragen der Lizenz bei der infoskop-Base.exe
- Integration in bestehende Client-Oberfläche

---

### Optimierungen

#### 2. Webframe-Ladeanzeige
**Ticket**: [INFO-1196](./details/info-1196.md)

Bei längeren Ladezeiten der Webframes (infoskop-Monitor und ::LEA) erhalten Nutzer nun eine „Bitte warten …" Anzeige.

**Verbesserungen**:
- ✅ Transparente Rückmeldung während Ladevorgang
- ✅ Professionelle Benutzererfahrung
- ✅ Verhindert Verwirrung bei längeren Ladezeiten
- ✅ Automatisches Verschwinden nach erfolgreichem Laden

**Details**: [Vollständige Dokumentation →](./details/info-1196.md)

---

### Fehlerbehebungen

#### 3. Splash-Anzeigen Deduplizierung
**Tickets**: [INFO-1192](./details/info-1192.md) | [QS-193](./details/qs-193.md)

Ein Problem wurde behoben, bei dem in Z1 mehrere gleichartige Splash-Anzeigen gleichzeitig geladen werden konnten.

**Fix**:
- ✅ Nur noch eine Anzeige pro Ausführung
- ✅ Singleton-Pattern implementiert
- ✅ Ressourcenoptimierung
- ✅ Saubere Benutzeroberfläche

**Details**: [Vollständige Dokumentation →](./details/info-1192.md)

**Related Testing**: [IT-257 Test Case](./details/it-257.md)

---

## Updater & Full-Setup

### Anpassungen

#### 1. Bonjour 32Bit entfernt
**Ticket**: [INFO-1188](./details/info-1188.md)

Die Installationsdatei für Bonjour 32Bit wurde entfernt. Das Produkt unterstützt ab sofort nur noch 64-Bit- und ARM-Systeme.

**Änderungen**:
- ❌ Bonjour 32-Bit entfernt
- ✅ Zwei 64-Bit-Installer hinzugefügt (Intel/ARM)
- ✅ Beide können parallel installiert werden
- ✅ Automatische Architektur-Erkennung

**Kompatibilität**:
- ✅ Windows 10/11 (64-Bit)
- ✅ Windows Server 2016/2019/2022 (64-Bit)
- ✅ ARM64-basierte Windows-Geräte
- ❌ 32-Bit-Systeme nicht mehr unterstützt

**Details**: [Vollständige Dokumentation →](./details/info-1188.md)

---

#### 2. Dienst-Namensgebung
Bei Installationen mit mehreren Bases auf einem Rechner wird der Standard-Dienstname „infoskop-Base" nun nicht mehr automatisch vergeben, um Konflikte zu vermeiden.

**Verhalten**:
- **Ohne `/MULTIPLEBASES` Flag**: Standard-Name "infoskop-Base"
- **Mit `/MULTIPLEBASES` Flag**: Individueller Name erforderlich

---

### Optimierungen

#### 3. Individuelle Dienstnamen
Der Updater kann nun individuelle Dienstnamen für Base und MediaServer übernehmen, um diese korrekt zu beenden und wieder zu starten.

**Parameter**:
```cmd
infoskop-Base-Updater.exe /bname "infoskop-Base-Praxis1" /mname "MediaServer-Praxis1"
```

**Vorteile**:
- Korrekte Dienstverwaltung bei Mehrfach-Installationen
- Updater kann spezifische Dienste steuern
- Keine manuellen Eingriffe erforderlich

**Siehe auch**:
- [INFO-1156 - Starter Dienst-Installation](./details/info-1156.md)
- [INFO-1157 - MediaServerStarter Dienst-Installation](./details/info-1157.md)

---

## Testing Documentation

Comprehensive test cases are available for critical features:

### Test Cases

#### IT-257: Base Updater - Manueller Update-Prozess
**[View Test Case →](./details/it-257.md)**

Validierung des manuellen Update-Prozesses über infoskop-Monitor, einschließlich:
- Splash-Anzeigen während Update
- Versionsprüfung
- Automatischer Client-Start

**Abdeckung**:
- Update-Verwaltung
- Splash-Anzeigen (nur eine pro Ausführung)
- Versionsverwaltung

---

#### IT-277: Online-Funktionen Deaktivierung
**[View Test Case →](./details/it-277.md)**

Umfassende Validierung der Deaktivierung aller Online-Funktionen.

**Abdeckung**:
- Onlineformulare (Formulare, Vorlagen, Systemvorlagen, Verschlüsselung)
- E-Mail-Funktionalität (Patienten, Posteingang/Postausgang, Dokumente)
- Auswertungen (PA-Cockpit, Bleaching-Cockpit)
- Stage1
- Re-Aktivierung und Wiederherstellung

**Related Tickets**:
- [AZUBI-403](./details/azubi-403.md)
- [AZUBI-421](./details/azubi-421.md)
- [QS-187](./details/qs-187.md)

---

## Migration Guide

### Von Version 4.x zu 5.0.0

#### Systemanforderungen

**Prüfen Sie VOR dem Update**:
1. ✅ System ist 64-Bit (Windows 10/11 oder Server 2016+)
2. ❌ 32-Bit-Systeme werden NICHT mehr unterstützt
3. ✅ Ausreichend Festplattenspeicher (mindestens 2 GB frei)
4. ✅ Admin-Rechte für Installation

---

#### Automatisches Update (empfohlen)

Via infoskop-Monitor:
1. Öffnen Sie infoskop-Monitor
2. Navigieren Sie zu **Administration** → **infoskop-Base Update**
3. Klicken Sie auf **"UPDATE MANUELL HINTERLEGEN"**
4. Wählen Sie `infoskop-Base-5.0.0-Updater.exe`
5. Bestätigen Sie den Update-Prozess
6. Warten Sie auf Splash-Anzeigen:
   - "Es wurden Updates für infoskop-Base gestartet"
   - "Updates abgeschlossen"

**Details**: [IT-257 Test Case](./details/it-257.md)

---

#### Manuelle Installation

Für Netzwerk-Deployments oder mehrere Systeme:
```cmd
# Standard-Installation
infoskop-Base-5.0.0-Updater.exe

# Mehrfach-Installation mit individuellen Dienstnamen
infoskop-Base-5.0.0-Updater.exe /MULTIPLEBASES /bname "infoskop-Base-Praxis1" /mname "MediaServer-Praxis1"
```

---

#### Nach dem Update

**Überprüfungen**:
1. ✅ Version prüfen (sollte 5.0.0 sein)
2. ✅ Dienste laufen:
   - infoskop-Base (oder individueller Name)
   - MediaServerStarter (falls verwendet)
   - HL7-Server (falls verwendet)
3. ✅ Bonjour-Dienst läuft
4. ✅ Lizenzen sind korrekt:
   - ::ORA-Lizenz (falls vorhanden)
   - ::LEA-Lizenz (bei Leistungskatalog)

**Neue Features testen**:
- [ ] Automatische Starter-Überwachung (läuft im Hintergrund)
- [ ] ::LEA (falls lizenziert)
- [ ] Webframe-Ladeanzeige
- [ ] Online-Funktionen Deaktivierung

---

#### Troubleshooting

**Problem**: Update schlägt fehl

**Lösung**:
1. Prüfen Sie Dienste (alle stoppen vor Update)
2. Prüfen Sie Admin-Rechte
3. Prüfen Sie Festplattenspeicher
4. Prüfen Sie Logdateien (`report.dat`, Logcheck)

---

**Problem**: Bonjour funktioniert nicht

**Lösung**:
1. Öffnen Sie `services.msc`
2. Suchen Sie "Bonjour Service"
3. Starten Sie den Dienst
4. Setzen Sie Starttyp auf "Automatisch"

**Details**: [INFO-1188 - Bonjour](./details/info-1188.md)

---

**Problem**: Dienste starten nicht

**Lösung**:
1. Prüfen Sie Dienstnamen in Base-Config:
   ```ini
   [Server]
   bname = <Ihr Dienst-Name>
   mname = <MediaServer Dienst-Name>
   ```
2. Passen Sie Updater-Parameter an (`/bname`, `/mname`)
3. Prüfen Sie Windows Event Log

**Details**: [INFO-1156 - Dienst-Installation](./details/info-1156.md)

---

## Support & Feedback

### Documentation Structure

All detailed documentation is organized in the `details/` folder:
- **AZUBI-xxx.md**: Training/Apprenticeship issues
- **QS-xxx.md**: Quality Assurance tickets
- **IT-xxx.md**: Test cases with detailed steps
- **INFO-xxx.md**: Information/General issues

### Quick Reference

| Component | Key Tickets | Documentation |
|-----------|-------------|---------------|
| infoskop-Base.exe | INFO-1243, QS-227 | E-Mail SMTP Validation |
| infoskop-Monitor | AZUBI-403, AZUBI-421, QS-187 | Online-Functions Control |
| infoskop::LEA | NEW in 5.0.0 | New Product |
| Starter.exe | INFO-1187, INFO-1156 | Auto-Monitoring, Service Installation |
| MediaServerStarter | INFO-1157 | Service Installation |
| VDDS-stage1.exe | INFO-1190, QS-218 | Evident Configuration |
| Infoskop-Client.exe | INFO-1192, INFO-1196, QS-193 | Splash Screens, Loading Display |
| Updater/Setup | INFO-1188 | Bonjour 64-Bit |

### Test Cases

| Test Case | Purpose | Documentation |
|-----------|---------|---------------|
| IT-257 | Update Process | [View](./details/it-257.md) |
| IT-277 | Online-Functions Deactivation | [View](./details/it-277.md) |

---

## Release Notes by Audience

Für zielgruppenspezifische Release Notes, siehe:
- **[TECHNIK](./release-notes-5.0.0-TECHNIK.md)** - Technische Details, Konfigurationsparameter
- **[SUPPORT](./release-notes-5.0.0-SUPPORT.md)** - Support-Hinweise, Troubleshooting
- **[VERTRIEB](./release-notes-5.0.0-VERTRIEB.md)** - Verkaufsargumente, Kundennutzen
- **[KUNDEN](./release-notes-5.0.0-KUNDEN.md)** - Benutzervorteile, neue Funktionen
- **[TRAINING](./release-notes-5.0.0-TRAINING.md)** - Schulungsfokus

---

**Document Version**: 1.0
**Last Updated**: November 2025
**Maintained by**: infoskop Development Team

---

© 2025 synmedico | infoskop-Base Version 5.0.0
