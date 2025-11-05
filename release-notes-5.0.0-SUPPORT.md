# Infoskop-Base Version 5.0.0 - Release Notes für Support

## Wichtige Fehlerbehebungen

### E-Mail-Versand (INFO-1243, QS-227)
**Problem**: E-Mails wurden als erfolgreich versendet angezeigt, obwohl SMTP-Server-Daten fehlerhaft waren.
**Lösung**: Validierung wurde verbessert. System prüft nun korrekt die Server-Antworten.
**Support-Hinweis**: Bei E-Mail-Problemen SMTP-Einstellungen überprüfen.

### Link-Öffnen im Browser (AZUBI-397, AZUBI-398, QS-177)
**Problem**: Links in E-Mail-/Vorlagentexten und Formularlinkbaukasten öffneten sich nicht im Browser.
**Lösung**: Link-Handling wurde korrigiert. Im Formularlinkbaukasten müssen Links jetzt direkt angeklickt werden.
**Support-Hinweis**: Kunden auf neues Verhalten beim Formularlinkbaukasten hinweisen.

### Preisübernahme mit Euro-Zeichen (QS-97)
**Problem**: PA- und Bleaching-Cockpit übernahm Preise mit € nicht korrekt.
**Lösung**: Behoben.
**Support-Hinweis**: Bekannte Tickets können geschlossen werden.

### ::ORA-Lizenzabfrage (INFO-1194)
**Problem**: Fehler bei der Lizenzabfrage.
**Lösung**: Behoben.
**Support-Hinweis**: Bei Lizenzproblemen Config-Einstellungen prüfen.

### Evident-Konfiguration (INFO-1190)
**Problem**: Automatische Evident-Konfiguration wurde nicht richtig erkannt.
**Lösung**: VDDS-stage1.exe behoben.

### Z1 Splash-Anzeigen (INFO-1192)
**Problem**: Mehrere gleichartige Splash-Anzeigen wurden gleichzeitig geladen.
**Lösung**: Nur noch eine Anzeige pro Ausführung möglich.

## Neue Funktionen - Support-relevant

### ::LEA (NEU)
**Beschreibung**: Neues Produkt für Leistungserfassung.
**Lizenzierung**: Automatisch bei korrekt hinterlegtem Leistungskatalog.
**Support-Hinweis**:
- Kunden benötigen korrekten Leistungskatalog
- Bei Problemen Leistungskatalog-Einstellungen prüfen
- Eigene Fensterinstanz im Client

### Automatische Base-Überwachung und Neustart (INFO-1187)
**Beschreibung**: Starter.exe überwacht Base automatisch und startet bei Problemen neu.
**Verhalten**:
- Timeout erhöht sich automatisch bei wiederholtem Auslösen
- Ermöglicht Erfolg bei langwierigen Operationen
- Protokollierung in report.dat und Logcheck

**Deaktivierung (falls nötig)**:
```ini
server/restartWhenUnresponsive=0
```

**Anpassung der Timeouts**:
```ini
server/lifesignToBaseInterval=5000        # Prüfintervall in ms
server/lifesignRestartBusyBaseAfterInterval=30000  # Timeout in ms
```

### HL7-Server sanftes Beenden
**Beschreibung**: HL7-Server wird beim Starter-Beenden sanft geschlossen.
**Vorteil**: Verhindert Netzwerkfehler und lange Timeouts.
**Aktivierung**:
```ini
# In Base-Config:
hl7/smartHandling=1
hl7/enabled=1
hl7/waitforclose=6000

# In HL7-Server Config:
server/useChilkatSockets=1
```
**Support-Hinweis**: Alte AppToStart-Einträge entfernen!

### Proxy-Konfiguration für Signexport
**Beschreibung**: Signexport kann nun über Proxy konfiguriert werden.
**Support-Hinweis**: Bei Verbindungsproblemen Proxy-Einstellungen prüfen.

## UI-Verbesserungen

### Monitor-Verbesserungen
- **Bildgrößenanpassung**: Embedded Bilder in E-Mails können jetzt angepasst werden
- **Icons aktualisiert**: Fehlende Cockpit-Icons ergänzt (QS-222)
- **Warnungseinstellungen**: Gesamtbearbeitung optimiert (AZUBI-399)
- **Offline-Modus**: Anzeigen bei deaktivierter Onlinefunktion verbessert (AZUBI-403, AZUBI-421, QS-187)
- **::ORA-Antwortfunktion**: Nur für ::ORA-Kunden sichtbar
- **Patientendaten-Löschung**: Ablauf optimiert (AZUBI-401)

### Client-Verbesserungen
- **"Bitte warten..."-Anzeige**: Bei verzögertem Webframe-Laden (Monitor, ::LEA) (INFO-1196)

## Installation & Update

### ⚠️ WICHTIG: 32-Bit-Unterstützung entfernt (INFO-1188)
**Änderung**: 32-Bit-Systeme werden nicht mehr unterstützt.
**Unterstützt**: Nur noch 64-Bit und ARM.
**Bonjour**: Zwei 64-Bit-Installer verfügbar (Intel und ARM), beide können parallel installiert werden.

**Support-Hinweis**:
- Vor Update Systemarchitektur prüfen!
- Bei 32-Bit-Systemen: Update nicht möglich, Kunde muss auf 64-Bit migrieren

### Mehrfachinstallationen
**Verbesserung**:
- Default-Dienstname "infoskop-Base" wird nur noch bei Einzelinstallationen verwendet
- Verhindert Konflikte bei mehreren Bases auf einem Rechner

**Dienst-Namen im Updater**:
```
/bname    Name des Base-Dienstes
/mname    Name des MediaServer-Dienstes
```

### Dienst-Installation verbessert (INFO-1156, INFO-1157)
**Problem**: Dienstnamen waren korrupt und für Windows nicht leserlich.
**Lösung**: Behoben in Starter.exe und MediaServerStarter.
**Neues Feature**: Dienstnamen werden in Base-Config gespeichert:
```ini
Server/bname    # Base-Dienst
Server/mname    # MediaServer-Dienst
```

## Troubleshooting-Hinweise

### E-Mail-Probleme
1. SMTP-Einstellungen überprüfen
2. Testmail versenden
3. Log-Einträge prüfen

### Base startet nicht / stürzt ab
1. `report.dat` prüfen
2. Logcheck durchführen
3. Wenn automatischer Neustart nicht gewünscht: `server/restartWhenUnresponsive=0`

### HL7-Verbindungsprobleme
1. Prüfen ob `hl7/smartHandling=1` gesetzt ist
2. `server/useChilkatSockets=1` im HL7-Server prüfen
3. AppToStart-Einträge entfernen

### ::LEA funktioniert nicht
1. Leistungskatalog korrekt hinterlegt?
2. Lizenzabfrage erfolgreich? (Logs prüfen)
3. Client-Version aktuell?

### Mehrfachinstallationen
1. Dienstnamen in Config prüfen (`Server/bname`, `Server/mname`)
2. Updater mit korrekten Parametern aufrufen (`/bname`, `/mname`)
3. Bei Default-Name Konflikten: `/MULTIPLEBASES` Flag verwenden

## Log-Dateien und Diagnose

### Neue/Geänderte Log-Quellen
- **report.dat**: Enthält jetzt Starter-Versuche, Base zu erreichen
- **Logcheck**: Übernimmt Inhalte aus report.dat
- **Base-Config**: Enthält jetzt Dienstnamen (`Server/bname`, `Server/mname`)
