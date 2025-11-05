# Infoskop-Base Version 5.0.0 - Release Notes für Technik

## infoskop-Base.exe

### Fehlerbehebung
- **E-Mail-Versand Validierung (INFO-1243, QS-227)**
  - Problem behoben: E-Mails wurden als erfolgreich versendet angezeigt, obwohl fehlerhafte SMTP-Serverdaten hinterlegt waren
  - Implementierung: Verbesserte Validierung der SMTP-Server-Antworten

## infoskop-Monitor

### Neue Funktionen
- **Bildgrößenanpassung in E-Mails (AZUBI-424)**
  - Embedded Bilder in Mail- und Vorlagentexten können nun in der Größe angepasst werden
  - Technische Details: Neue UI-Steuerelemente für Bildgrößenanpassung

### Fehlerbehebungen
- **Link-Handling (AZUBI-397, AZUBI-398, QS-177)**
  - Links in Mail-/Vorlagentexten und Formularlinkbaukasten öffnen sich nun korrekt im lokalen Browser
  - Formularlinkbaukasten: Links müssen nun direkt angeklickt werden für Vorschau
- **Preisübernahme (QS-97)**
  - PA- und Bleaching-Cockpit: Preisübernahme funktioniert nun auch mit Euro-Zeichen (€)
- **::ORA-Lizenz (INFO-1194)**
  - Fehler bei der Lizenzabfrage behoben

### Optimierungen
- **UI-Verbesserungen**
  - Fehlende Icons in Cockpits ergänzt und aktualisiert (QS-222)
  - Gesamtbearbeitung in Warnungseinstellungen optimiert (AZUBI-399)
  - Anzeigen bei deaktivierter Onlinefunktion angepasst (AZUBI-403, AZUBI-421, QS-187)
- **Patientendaten-Löschung (AZUBI-401)**
  - Ablauf optimiert und angepasst
- **::ORA-Antwortfunktion**
  - Nur für ::ORA-Kunden aktiv, für andere deaktiviert

## infoskop::LEA (NEU)

### Neue Produkteinführung
- Webframe-Einbindung für Client
- Base-Funktionen für Anfragenverwaltung und Datenhaltung
- **Automatische Lizenzierung**: Aktiviert sich automatisch bei korrekt hinterlegtem Leistungskatalog

## Signexport.exe

### Neue Funktionen
- **Proxy-Konfiguration**: Option zur Konfiguration eines Proxy-Servers hinzugefügt

## MediaServerStarter

### Optimierungen
- **Dienst-Installation (INFO-1157)**
  - Fehler behoben: Dienstnamen waren korrupt und für Windows nicht leserlich
  - Verbesserte Installation als Windows-Dienst
- **Mehrfachinstallationen**
  - Dienstnamen werden in Base-Config gespeichert
  - Config-Parameter: `Server/mname` (Name des MediaServer-Dienstes)

## VDDS-stage1.exe

### Fehlerbehebungen
- **Evident-Konfiguration (INFO-1190)**
  - Automatische Evident-Konfiguration wird nun korrekt erkannt

## Starter.exe

### Neue Funktionen
- **Automatische Überwachung und Neustart (INFO-1187)**
  - TCP-Socket-Server der infoskop-Base.exe wird automatisch überwacht
  - Automatischer Neustart nach Timeout
  - Timeout erhöht sich bei wiederholtem Eintritt (ermöglicht Erfolg bei langwierigen Aktionen)

#### Configuration Flags (Base-config):
```ini
server/restartWhenUnresponsive=1
# 0 = Automatischer Neustart deaktiviert

server/lifesignToBaseInterval=5000
# Intervall für Socket-Server-Prüfung (in ms)

server/lifesignRestartBusyBaseAfterInterval=30000
# Timeout vor Neustart (in ms), erhöht sich automatisch bei wiederholtem Auslösen
```

### Optimierungen
- **Dienst-Installation (INFO-1156)**
  - Fehler mit korrupten Dienstnamen behoben
- **Mehrfachinstallationen**
  - Dienstnamen werden in Base-Config gespeichert
  - Config-Parameter:
    - `Server/bname` (Name des infoskop-Base-Dienstes)
    - `Server/mname` (Name des MediaServer-Dienstes)
- **Fehlerprotokollierung (INFO-1187)**
  - Versuche, Base zu erreichen, werden in `report.dat` dokumentiert
  - Inhalt wird in Logcheck übertragen
- **HL7-Server-Überwachung**
  - Automatische Überwachung unabhängig von AppToStart
  - Sanftes Beenden beim Starter-Shutdown
  - Verhindert Netzwerkfehler und lange Timeouts
  - **WICHTIG**: Benötigt `server/useChilkatSockets` Flag im HL7-Server

#### Configuration Flags (Base-config):
```ini
hl7/smartHandling=0
# 1 = Automatische Überwachung und sanftes Beenden aktiviert
# Vorher Einträge aus AppToStart entfernen
# Benötigt: hl7/enabled=1

hl7/waitforclose=6000
# Wartezeit für sanftes Beenden (in ms), 0 = deaktiviert
```

## HL7-Server

### Neue Funktionen
- **Sanftes Schließen des Socket-Servers**
  - Ermöglicht ordnungsgemäßes Schließen vor Beendigung
  - Details siehe Starter.exe

#### Configuration Flags (HL7-Server config):
```ini
server/useChilkatSockets=0
# Wechsel auf neuere Socket-Implementation
# Voraussetzung für sanftes Schließen
# Wird automatisch aktiviert wenn: module/orbis=1 UND server/openstream=1
```

## Infoskop-Client.exe

### Neue Funktionen
- **::LEA-Unterstützung**
  - Windows-Applikation als eigenständige Fensterinstanz
  - Lizenzabfrage bei infoskop-Base.exe
- **Webframe-Ladevorgang (INFO-1196)**
  - "Bitte warten..."-Anzeige bei verzögerter Webframe-Anzeige (Monitor und ::LEA)

### Fehlerbehebungen
- **Z1 Splash-Anzeigen (INFO-1192)**
  - Nur noch eine Splash-Anzeige pro Ausführung möglich

## Updater und Full-Setup

### Wichtige Änderungen
- **Bonjour 32-bit entfernt (INFO-1188)**
  - ⚠️ **BREAKING**: Nur noch 64-Bit- und ARM-Systeme werden unterstützt
  - Zwei 64-Bit-Installationsdateien verfügbar (Intel und ARM)
  - Beide Installer können parallel und in beliebiger Reihenfolge installiert werden

### Optimierungen
- **Mehrfachinstallationen**
  - Default-Dienstname "infoskop-Base" wird nur noch ohne `/MULTIPLEBASES` Flag verwendet
- **Dienst-Namen-Übergabe**
  - Neue Parameter: `/bname` (Base) und `/mname` (MediaServer)
  - Ermöglicht korrektes Beenden und Starten von Diensten mit abweichenden Namen

## Systemanforderungen

### Neu ab Version 5.0.0
- **Minimale Systemarchitektur**: 64-Bit oder ARM
- **Nicht mehr unterstützt**: 32-Bit-Systeme
