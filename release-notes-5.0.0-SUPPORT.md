# Release Notes Base 5.0.0 - SUPPORT

## Wichtige Fehlerbehebungen

### E-Mail-Versand (QS-227)
**Problem behoben**: E-Mails wurden trotz leerer oder fehlerhafter SMTP-Serverdaten als erfolgreich versendet angezeigt.
- **Support-Hinweis**: Falls Kunden melden, dass E-Mails nicht ankommen, prüfen Sie die SMTP-Konfiguration. Das System zeigt nun korrekt an, wenn der Versand fehlschlägt.

### Links in E-Mails und Vorlagen (QS-177)
**Problem behoben**: Links in E-Mail- und Vorlagentexten sowie im Formularlinkbaukasten konnten nicht im lokalen Browser geöffnet werden.
- **Verhaltensänderung**: Im Formularlinkbaukasten müssen Links nun direkt angeklickt werden für eine Vorschau.

### Preisübernahme PA- und Bleaching-Cockpit (QS-97)
**Problem behoben**: Preisübernahme funktionierte nicht korrekt, wenn der Preis ein Euro-Zeichen (€) enthielt.
- **Support-Hinweis**: Dieses Problem sollte nun behoben sein. Bei Problemen mit der Preisübernahme bitte andere Ursachen prüfen.

### Splash-Anzeigen in Z1 (QS-193)
**Problem behoben**: In Z1 konnten mehrere gleichartige Splash-Anzeigen gleichzeitig geladen werden.
- **Verhaltensänderung**: Pro Ausführung wird nur noch eine Anzeige angezeigt.

### Evident-Konfiguration (QS-218)
**Problem behoben**: Automatische Evident Konfiguration wurde nicht richtig erkannt.

## Neue Funktionen und Produkte

### ::LEA - Neues Produkt
- **Neu verfügbar**: ::LEA steht nun zur Verfügung
- Die Lizenzierung erfolgt automatisch nach korrekter Einrichtung
- Unterstützung in Infoskop-Client.exe implementiert
- **Support-Hinweis**: Bei Fragen zur Einrichtung siehe [TODO: Installationsanleitung ergänzen]

### Bildgrößenanpassung in E-Mails und Vorlagen
- Anwender können nun die Größe eingebetteter Bilder in E-Mail- und Vorlagentexten flexibel anpassen
- **Support-Hinweis**: [TODO: Anleitung zur Bildgrößenanpassung ergänzen]

### Selbstüberwachung Starter.exe
- Der Starter überwacht nun automatisch seine Funktionsfähigkeit und startet sich bei Problemen selbstständig neu
- **Support-Hinweis**: Sollte zu weniger Ausfällen führen. Bei wiederkehrenden Problemen `report.dat` prüfen.

### Ladeanzeige für Webframes
- Bei längeren Ladezeiten in infoskop-Monitor und ::LEA wird nun eine „Bitte warten …"-Anzeige gezeigt
- **Support-Hinweis**: Kunden sollten weniger häufig denken, das System sei eingefroren.

## Wichtige Anpassungen

### Antwortfunktion nur für ::ORA-Kunden
- Die Antwortfunktion ist nur für ::ORA-Kunden aktiv
- Für andere Nutzer wurde die Anzeige angepasst und die Funktion deaktiviert
- **Support-Hinweis**: Falls Kunden die Antwortfunktion vermissen, prüfen Sie ob ::ORA-Lizenz vorhanden ist.

### Offline-Anzeigen optimiert (QS-187)
- Anzeigen bei deaktivierter Onlinefunktion wurden optimiert
- **Support-Hinweis**: [TODO: Details zu den Änderungen ergänzen]

### Icons in Cockpits aktualisiert (QS-222)
- Fehlende Icons in den Cockpits wurden ergänzt und aktualisiert

## Verbesserungen

### Warnungseinstellungen - Gesamtbearbeitung
- Das Anzeigeverhalten der Gesamtbearbeitung wurde verbessert
- Betrifft: Umschalten zwischen „Warnungen", „Anamnese" und „Alle" sowie Nutzung der „Alles Ja/Nein"-Option

### HL7-Server
- Sanftes Schließen implementiert - sollte Netzwerkprobleme und lange Timeouts vermeiden
- HL7-Server werden nun automatisch vom Starter überwacht

### Fehlerprotokollierung
- Der Starter protokolliert seine Versuche in `report.dat` (bei Problemen Base zu erreichen)
- Diese Informationen werden auch in den Logcheck übernommen
- **Support-Hinweis**: Bei Verbindungsproblemen `report.dat` für Diagnose nutzen

## Systemanforderungen / Installationshinweise

### Bonjour - Nur noch 64-Bit und ARM
- **WICHTIG**: Bonjour 32Bit wird nicht mehr unterstützt
- Das Produkt unterstützt ab sofort nur noch 64-Bit- und ARM-Systeme
- Neue Installationsdatei für Bonjour 64Bit unterstützt beide Architekturen (Intel und ARM)
- **Support-Hinweis**: Bei 32-Bit-Systemen ist ein Upgrade auf 64-Bit erforderlich

### Mehrfach-Installationen
- Bei mehreren Bases auf einem Rechner wird der Standard-Dienstname „infoskop-Base" nicht mehr automatisch vergeben
- Verhindert Konflikte zwischen verschiedenen Installationen
- **Support-Hinweis**: Bei Dienst-Problemen prüfen, ob individuelle Dienstnamen konfiguriert sind

## Technische Verbesserungen (für komplexe Support-Fälle)

### Proxy-Konfiguration Signexport.exe
- Option hinzugefügt, um einen Proxy zu konfigurieren
- **Support-Hinweis**: [TODO: Konfigurationsanleitung ergänzen]

### MediaServerStarter Dienst-Installation
- Fehler mit unleserlichen Dienstnamen unter Windows wurde behoben
- Dienstnamen werden in Base-Config gespeichert für Mehrfachinstallationen

### Updater - Individuelle Dienstnamen
- Der Updater kann nun individuelle Dienstnamen für Base und MediaServer übernehmen
- Parameter: `/bname` (Base) und `/mname` (MediaServer)

---
*Support-Dokumentation - Fokus auf Kundensupport und Problemlösung*
