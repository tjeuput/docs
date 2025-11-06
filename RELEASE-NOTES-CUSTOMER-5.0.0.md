# infoskop-Base 5.0.0 Release Notes

**Release Date:** September 2025
**Target Audience:** Customers and End Users

---

## Übersicht

Version 5.0.0 bringt wichtige Verbesserungen in den Bereichen Stabilität, E-Mail-Kommunikation, Benutzerführung und Integration. Zusätzlich wird das neue Produkt infoskop::LEA eingeführt.

**Wichtigste Änderungen:**
- Neues Produkt: infoskop::LEA für Leistungsabrechnung
- Automatische Systemüberwachung für höhere Verfügbarkeit
- Verbesserte E-Mail-Validierung
- Konsistente Kontrolle über Online-Funktionen
- Nur noch 64-Bit Systeme werden unterstützt

---

## Neue Funktionen

### infoskop::LEA (Neues Produkt)

Ein neues Modul für die Leistungsabrechnung steht zur Verfügung. Die Lizenz aktiviert sich automatisch bei korrekt hinterlegtem Leistungskatalog.

**Funktionsumfang:**
- Webframe-Integration im Client
- Verwaltung von Anfragen und Datenhaltung in der Base
- Automatische Lizenzierung

**Referenz:** ReleaseNote.md, Abschnitt "Infoskop::LEA" und "Infoskop-Client.exe"

---

### Bildgrößenanpassung in E-Mails und Vorlagen

Sie können jetzt die Größe von eingebetteten Bildern in Mail- und Vorlagentexten direkt im Editor anpassen. Bilder können per Drag & Drop eingefügt werden.

**Nutzen:** Flexiblere Gestaltung von E-Mails und Dokumenten.

**Referenz:** ReleaseNote.md, Abschnitt "Infoskop-Monitor"

---

### Automatische Systemüberwachung

Das System überwacht sich selbst und startet bei Problemen automatisch neu. Diese Funktion ist standardmäßig aktiviert und läuft im Hintergrund.

**Funktionsweise:**
- Prüfung der Base-Erreichbarkeit alle 5 Sekunden
- Automatischer Neustart nach 30 Sekunden Nicht-Erreichbarkeit
- Timeout erhöht sich adaptiv bei wiederholten Problemen
- Protokollierung in report.dat und Logcheck

**Nutzen:** Höhere Systemverfügbarkeit, weniger manuelle Eingriffe erforderlich.

**Referenz:** [INFO-1187](./details/info-1187.md) | ReleaseNote.md, Abschnitt "Starter.exe"

---

### Ladeanzeige für Webframes

Beim Laden von infoskop-Monitor oder infoskop::LEA wird eine "Bitte warten..."-Anzeige gezeigt.

**Nutzen:** Klarheit über den Ladestatus, keine Unsicherheit bei längeren Ladezeiten.

**Referenz:** [INFO-1196](./details/info-1196.md) | ReleaseNote.md, Abschnitt "Infoskop-Client.exe"

---

## Fehlerbehebungen

### E-Mail-Versandstatus

Ein Fehler wurde behoben, durch den E-Mails als erfolgreich versendet angezeigt wurden, obwohl fehlerhafte SMTP-Serverdaten hinterlegt waren.

**Problem:** Falsche Erfolgsrückmeldung bei ungültiger E-Mail-Konfiguration.
**Lösung:** Validierung der SMTP-Einstellungen vor dem Versand. Bei Fehlern wird eine klare Fehlermeldung angezeigt.

**Nutzen:** Zuverlässige Rückmeldung über tatsächlichen Versandstatus.

**Referenz:** [INFO-1243](./details/info-1243.md) | [QS-227](./details/qs-227.md)

---

### Link-Handling in E-Mails und Vorlagen

Links in Mail- und Vorlagentexten sowie im Formularlinkbaukasten öffnen sich jetzt korrekt im lokalen Browser. Das Verhalten im Formularlinkbaukasten wurde angepasst: Links müssen direkt angeklickt werden.

**Nutzen:** Funktionale Links, intuitivere Bedienung.

**Referenz:** [QS-177](./details/qs-177.md)

---

### Preisübernahme mit Euro-Zeichen

Die Preisübernahme im PA- und Bleaching-Cockpit funktioniert jetzt auch korrekt, wenn der Preis ein Euro-Zeichen (€) enthält.

**Referenz:** [QS-97](./details/qs-97.md)

---

### Online-Funktionen Kontrolle

Die Deaktivierung von Online-Funktionen wird jetzt konsistent durchgesetzt:
- E-Mail-Versand ist komplett blockiert bei Deaktivierung
- Onlineformular-Einstellungen sind nicht mehr zugänglich
- Konsistentes Verhalten in infoskop-Base, Monitor und App

**Problem vorher:** E-Mails wurden trotz Deaktivierung versendet, Einstellungen waren noch zugänglich.
**Nutzen:** Echte Kontrolle über Online-Funktionen, wichtig für Datenschutz.

**Referenz:** [AZUBI-403](./details/azubi-403.md) | [AZUBI-421](./details/azubi-421.md) | [QS-187](./details/qs-187.md) | [Test IT-277](./details/it-277.md)

---

### Splash-Anzeigen

Bei Z1 konnten zu viele gleichartige Splash-Anzeigen geladen werden. Jetzt ist nur noch eine Anzeige pro Ausführung möglich.

**Referenz:** [INFO-1192](./details/info-1192.md) | [QS-193](./details/qs-193.md)

---

### infoskop::ORA-Lizenz

Fehler bei der Abfrage der infoskop::ORA-Lizenz wurde behoben.

**Nutzen:** Korrekte Freischaltung von ::ORA-Funktionen für lizenzierte Kunden.

**Referenz:** [INFO-1194](./details/info-1194.md)

---

### Evident-Integration

Die automatische Evident-Konfiguration erkennt die Installation nun zuverlässiger.

**Betrifft:** Praxen, die Evident als Praxisverwaltungssystem nutzen.
**Nutzen:** Automatische Konfiguration funktioniert, weniger manuelle Eingriffe.

**Referenz:** [INFO-1190](./details/info-1190.md) | [QS-218](./details/qs-218.md)

---

### Dienst-Installation

Fehler bei der Installation als Windows-Dienst wurden behoben. Dienstnamen waren korrupt und nicht für Windows leserlich.

**Betrifft:** Starter.exe, MediaServerStarter
**Nutzen:** Korrekte Dienstverwaltung, besonders bei Mehrfach-Installationen.

**Referenz:** [INFO-1156](./details/info-1156.md) | [INFO-1157](./details/info-1157.md)

---

## Optimierungen

### Warnungseinstellungen

Die Gesamtbearbeitung in den Warnungseinstellungen wurde optimiert. Das Anzeigeverhalten beim Umschalten zwischen Tabs ist nun konsistent.

**Referenz:** [AZUBI-399](./details/azubi-399.md)

---

### Patientendaten-Löschung

Der Ablauf der Löschung von Patientendaten wurde angepasst und optimiert.

**Referenz:** ReleaseNote.md, Abschnitt "Infoskop-Monitor"

---

### Cockpit-Icons

Fehlende Icons in den Cockpits wurden ergänzt und aktualisiert.

**Nutzen:** Vollständige, moderne Darstellung.

**Referenz:** [QS-222](./details/qs-222.md)

---

### Offline-Anzeigen

Die Anzeigen bei deaktivierter Onlinefunktion wurden angepasst für klarere Benutzerführung.

**Referenz:** [QS-187](./details/qs-187.md)

---

## Systemanforderungen

### Wichtige Änderung: Nur noch 64-Bit

Ab Version 5.0.0 werden nur noch 64-Bit-Systeme unterstützt.

**Unterstützt:**
- Windows 10/11 (64-Bit)
- Windows Server 2016 oder neuer (64-Bit)
- ARM64-basierte Windows-Systeme

**Nicht mehr unterstützt:**
- 32-Bit-Systeme

**Bonjour-Installation:**
- 32-Bit-Installer wurde entfernt
- Zwei 64-Bit-Installer (Intel/ARM) werden bereitgestellt
- Beide können parallel installiert werden

**Referenz:** [INFO-1188](./details/info-1188.md)

---

## Update-Prozess

### Via infoskop-Monitor

1. Öffnen Sie infoskop-Monitor
2. Navigation: Administration → infoskop-Base Update
3. Klicken Sie auf "UPDATE MANUELL HINTERLEGEN"
4. Wählen Sie die Updater-Datei (infoskop-Base-5.0.0-Updater.exe)
5. Bestätigen Sie den Update-Prozess

**Anzeigen während des Updates:**
- "Es wurden Updates für infoskop-Base gestartet" (während Installation)
- "Updates abgeschlossen" (nach erfolgreichem Update)

**Referenz:** [Test IT-257](./details/it-257.md)

---

### Für Mehrfach-Installationen

Der Updater unterstützt jetzt individuelle Dienstnamen über Parameter `/bname` und `/mname`.

**Beispiel:**
```
infoskop-Base-Updater.exe /bname "infoskop-Base-Praxis1" /mname "MediaServer-Praxis1"
```

**Referenz:** ReleaseNote.md, Abschnitt "Infoskop-Base-Updater und infoskop-Base-Setup"

---

## Weitere Änderungen

### Signexport.exe
- Option zur Proxy-Konfiguration hinzugefügt

### HL7-Server
- Unterstützung für sanftes Schließen des Socket-Servers
- Vermeidet Netzwerkfehler mit langen Timeouts

**Referenz:** ReleaseNote.md, Abschnitte "Signexport.exe" und "HL7-Server"

---

## Prüfung nach dem Update

### Empfohlene Checks

1. **Versionsprüfung**
   - infoskop-Monitor: Administration → infoskop-Base Update
   - Installierte Version sollte 5.0.0 anzeigen

2. **Dienste prüfen**
   - Windows Services (services.msc) öffnen
   - Prüfen: infoskop-Base, MediaServerStarter, Bonjour-Dienst laufen

3. **Funktionstest**
   - E-Mail-Versand testen (an sich selbst)
   - Online-Funktionen prüfen (falls genutzt)
   - ::LEA aufrufen (falls lizenziert)

---

## Häufige Fragen

### Bleiben meine Einstellungen erhalten?

Ja. Alle Einstellungen, Patientendaten und Konfigurationen bleiben beim Update erhalten.

---

### Wie lange dauert das Update?

Etwa 5-10 Minuten, abhängig vom System.

---

### Muss ich 64-Bit haben?

Ja. Ab Version 5.0.0 sind nur noch 64-Bit-Systeme kompatibel. Die meisten modernen Systeme sind bereits 64-Bit.

**Prüfung:** Rechtsklick auf "Dieser PC" → Eigenschaften → unter "Systemtyp" steht "64-Bit-Betriebssystem"

---

### Funktioniert die automatische Überwachung immer?

Ja, sie läuft standardmäßig im Hintergrund. Falls Sie sie deaktivieren möchten (nicht empfohlen), kontaktieren Sie den Support.

---

### Was ist mit meinen E-Mail-Einstellungen nach dem Update?

Ihre E-Mail-Konfiguration bleibt erhalten. Falls Sie nach dem Update Fehlermeldungen beim E-Mail-Versand bekommen, bedeutet das, dass Ihre SMTP-Einstellungen korrigiert werden müssen. Dies war vorher nicht sichtbar.

---

## Support

Bei Fragen oder Problemen wenden Sie sich bitte an:

**E-Mail:** support@synmedico.de
**Telefon:** [Ihre Support-Hotline]

**Dokumentation:**
- Vollständige technische Dokumentation: [RELEASE-DOCUMENTATION-5.0.0.md](./RELEASE-DOCUMENTATION-5.0.0.md)
- Technische Release Notes: [release-notes-5.0.0-TECHNIK.md](./release-notes-5.0.0-TECHNIK.md)
- Detail-Dokumentation: [details/](./details/)

---

**Version:** 5.0.0
**Datum:** November 2025
© 2025 synmedico | infoskop-Base
