# Release Notes Base 5.0.0 - SUPPORT
## Vorläufige Version (Interner Gebrauch)

## Kritische Fehlerbehebungen

### E-Mail-Versand - Falsche Statusmeldungen (QS-227)
**Problem behoben**: Das System zeigte E-Mails fälschlicherweise als erfolgreich versendet an, selbst wenn die SMTP-Serverdaten leer oder fehlerhaft waren.

**Support-Hinweis**:
- Falls Kunden berichten, dass E-Mails nicht beim Empfänger ankommen, prüfen Sie zunächst die SMTP-Konfiguration
- Das System zeigt nun korrekt Fehler beim Versand an - achten Sie auf entsprechende Fehlermeldungen
- Bei Versandproblemen: SMTP-Server, Port, Authentifizierung und Verschlüsselung überprüfen

### Link-Probleme in E-Mails und Vorlagen (QS-177)
**Problem behoben**: Links konnten nicht im lokalen Browser geöffnet werden - betraf E-Mail-Texte, Vorlagentexte und den Formularlinkbaukasten.

**Verhaltensänderung im Formularlinkbaukasten**:
- Links müssen nun direkt angeklickt werden, um eine Vorschau zu erhalten
- Vorheriges Verhalten: Vorschau wurde möglicherweise beim Hovern oder anderen Interaktionen angezeigt

**Support-Hinweis**: Falls Kunden sich über das geänderte Verhalten beschweren, erklären Sie, dass dies zur Verbesserung der Benutzerführung implementiert wurde.

### Preisübernahme mit Euro-Zeichen (QS-97)
**Problem behoben**: Die Preisübernahme im PA- und Bleaching-Cockpit funktionierte nicht korrekt, wenn der Preis ein €-Zeichen enthielt.

**Support-Hinweis**:
- Dieser Bug sollte nun vollständig behoben sein
- Falls weiterhin Probleme mit der Preisübernahme auftreten, prüfen Sie andere mögliche Ursachen (Datenbankeinträge, Berechtigungen, etc.)

### Mehrfache Splash-Anzeigen in Z1 (QS-193)
**Problem behoben**: In Z1 konnten mehrere identische Splash-Anzeigen gleichzeitig erscheinen, was verwirrend für Nutzer war.

**Verhaltensänderung**: Pro Programmausführung wird nur noch eine einzelne Splash-Anzeige gezeigt.

### Evident-Konfigurationserkennung (QS-218)
**Problem behoben**: Die automatische Erkennung der Evident-Konfiguration funktionierte nicht zuverlässig.

**Support-Hinweis**: Bei Evident-Integrationsproblemen sollte die automatische Erkennung nun korrekt funktionieren. Falls Probleme auftreten, überprüfen Sie die Konfigurationsdateien manuell.

## Neue Funktionen und Produkte

### ::LEA - Neues Produkt verfügbar
**Neu**: Das Produkt ::LEA ist jetzt verfügbar und wird nach erfolgreicher Einrichtung automatisch lizenziert.

**Support-Hinweis**:
- Die Lizenzierung erfolgt automatisch - keine manuelle Aktivierung erforderlich
- Voraussetzung: Korrekte Einrichtung muss abgeschlossen sein
- ::LEA-Support in Infoskop-Client.exe ist implementiert
- Bei längeren Ladezeiten erscheint automatisch eine "Bitte warten..."-Anzeige

### Bildgrößenanpassung in E-Mails und Vorlagen
**Neu**: Nutzer können jetzt die Größe von eingebetteten Bildern in E-Mail- und Vorlagentexten flexibel anpassen.

**Support-Hinweis**:
- Diese Funktion ermöglicht professionellere E-Mail-Gestaltung
- Bei Fragen zur Nutzung: Benutzer kann Bilder durch Ziehen der Ecken oder über Kontextmenü anpassen

### Automatische Selbstüberwachung (Starter.exe)
**Neu**: Der Starter überwacht sich nun selbst und startet automatisch neu, falls Probleme auftreten.

**Support-Hinweis**:
- Dies sollte zu deutlich weniger Systemausfällen führen
- Bei wiederkehrenden Neustarts: Prüfen Sie die Datei `report.dat` für Details zu den Problemen
- Die Informationen aus `report.dat` werden auch in den Logcheck übernommen

### Verbesserte Ladeanzeigen
**Neu**: Bei längeren Ladezeiten in infoskop-Monitor und ::LEA erscheint eine "Bitte warten..."-Anzeige.

**Support-Hinweis**:
- Reduziert Kundenanrufe wegen vermeintlich eingefrorener Systeme
- Nutzer sehen nun klar, dass das System arbeitet und nicht abgestürzt ist

## Wichtige Anpassungen

### Antwortfunktion - Nur für ::ORA-Kunden
**Geändert**: Die Antwortfunktion ist nur noch für Kunden mit ::ORA-Lizenz sichtbar und aktiv.

**Support-Hinweis**:
- Nicht-::ORA-Kunden sehen diese Funktion nicht mehr in der Oberfläche
- Falls Kunden die Funktion vermissen: Prüfen Sie, ob eine ::ORA-Lizenz vorhanden ist
- Ggf. Upselling-Möglichkeit für ::ORA

### Optimierte Offline-Anzeigen (QS-187)
**Verbessert**: Die Anzeigen bei deaktivierter Onlinefunktion wurden überarbeitet.

**Support-Hinweis**: Kunden sollten nun klarere Hinweise erhalten, wenn sie im Offline-Modus arbeiten.

### Aktualisierte Cockpit-Icons (QS-222)
**Verbessert**: Fehlende Icons in den Cockpits wurden ergänzt und vorhandene aktualisiert.

**Support-Hinweis**: Kunden könnten sich über leicht veränderte Symbole wundern - dies ist beabsichtigt und dient der Modernisierung der Oberfläche.

## Verbesserungen für stabilere Systeme

### Verbesserte Warnungseinstellungen
**Optimiert**: Das Anzeigeverhalten der Gesamtbearbeitung in den Warnungseinstellungen wurde verbessert.

**Betroffene Bereiche**:
- Umschalten zwischen "Warnungen", "Anamnese" und "Alle"
- Verwendung der "Alles Ja/Nein"-Option

### HL7-Server - Sanftes Herunterfahren
**Verbessert**:
- HL7-Server werden nun vom Starter automatisch überwacht
- Beim Beenden erfolgt ein kontrolliertes Herunterfahren (graceful shutdown)

**Support-Hinweis**: Dies verhindert Netzwerkprobleme und lange Timeouts beim Beenden des Systems. Sollten weiterhin HL7-Verbindungsprobleme auftreten, prüfen Sie andere Ursachen.

### Verbesserte Fehlerdiagnose
**Neu**: Der Starter protokolliert alle Verbindungsversuche zur Base in `report.dat`.

**Support-Hinweis**:
- Bei Verbindungsproblemen zwischen Starter und Base: `report.dat` auslesen für detaillierte Diagnoseinformationen
- Diese Daten sind auch im Logcheck verfügbar
- Erleichtert die Remote-Diagnose erheblich

## Systemanforderungen und Installation

### Wichtig: Nur noch 64-Bit und ARM
**Breaking Change**: Bonjour 32Bit wird nicht mehr unterstützt!

**Support-Hinweis**:
- Das Produkt unterstützt ab Version 5.0.0 nur noch 64-Bit- und ARM-Systeme
- Bei 32-Bit-Systemen ist ein Upgrade auf 64-Bit erforderlich
- Falls Kunden noch 32-Bit verwenden: Migration auf 64-Bit-Hardware/OS notwendig
- Die neue Bonjour 64Bit-Installation unterstützt Intel x64 und ARM64

### Mehrfach-Installationen - Dienst-Namensgebung
**Geändert**: Bei mehreren Bases auf einem Rechner wird der Standard-Dienstname "infoskop-Base" nicht mehr automatisch vergeben.

**Support-Hinweis**:
- Verhindert Konflikte bei Mehrfachinstallationen
- Bei Dienst-Problemen: Prüfen Sie, ob individuelle Dienstnamen konfiguriert sind
- MediaServerStarter und Starter speichern Dienstnamen nun in der Base-Config

## Technische Verbesserungen (für komplexe Support-Fälle)

### Proxy-Konfiguration (Signexport.exe)
**Neu**: Möglichkeit zur Konfiguration eines Proxy-Servers wurde hinzugefügt.

**Support-Hinweis**: Für Kunden in Netzwerkumgebungen mit Proxy-Anforderungen relevant.

### MediaServerStarter - Dienst-Installation
**Verbessert**:
- Fehler mit unleserlichen Dienstnamen unter Windows wurde behoben
- Dienstnamen werden in Base-Config persistiert

### Updater - Individuelle Dienstnamen
**Neu**: Der Updater kann individuelle Dienstnamen verarbeiten.

**Kommandozeilenparameter**:
- `/bname` für Base-Dienst
- `/mname` für MediaServer-Dienst

**Support-Hinweis**: Bei Update-Problemen in Mehrfach-Installationen: Stellen Sie sicher, dass die korrekten Dienstnamen als Parameter übergeben werden.

## Support-Checkliste für Version 5.0.0

**Bei E-Mail-Problemen**:
1. SMTP-Konfiguration überprüfen
2. Fehlermeldungen im System prüfen (werden nun korrekt angezeigt)
3. Testversand durchführen

**Bei Link-Problemen**:
1. Browser-Einstellungen prüfen
2. Neues Verhalten im Formularlinkbaukasten erklären

**Bei Systemstabilitätsproblemen**:
1. `report.dat` auslesen
2. Logcheck prüfen
3. Selbstüberwachung sollte automatische Neustarts durchführen

**Bei Evident-Problemen**:
1. Automatische Erkennung sollte nun funktionieren
2. Manuelle Konfigurationsprüfung als Fallback

**Bei Installationsproblemen**:
1. 64-Bit-Systemvoraussetzung prüfen
2. Bei Mehrfachinstallationen: Dienstnamen-Konfiguration prüfen

---
*Support-Dokumentation - Fokus auf Kundensupport und Problemlösung*
*Basiert auf vorläufigen Release Notes - Stand: Interner Review*
