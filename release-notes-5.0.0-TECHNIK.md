# Release Notes Base 5.0.0 - TECHNIK

## infoskop-Base.exe

### Fehlerbehebung
1. **QS-227**: E-Mail-Versandstatus - Ein Problem wurde behoben, durch das E-Mails trotz leerer oder fehlerhafter SMTP-Serverdaten als erfolgreich versendet angezeigt wurden.

## infoskop-Monitor

### Neue Funktionen
1. Flexible Bildgrößenanpassung - Anwender können nun die Größe eingebetteter Bilder in E-Mail- und Vorlagentexten flexibel anpassen, um Inhalte besser zu gestalten.

### Fehlerbehebungen
2. **QS-177**: Link-Handling - Ein Problem wurde behoben, das das Öffnen von Links in E-Mail- und Vorlagentexten sowie im Formularlinkbaukasten im lokalen Browser verhinderte. Zudem wurde das Verhalten im Formularlinkbaukasten angepasst, sodass Links nun direkt angeklickt werden müssen für eine Vorschau.
7. **QS-97**: Preisübernahme - Die Preisübernahme im PA- und Bleaching-Cockpit funktioniert nun auch korrekt, wenn der Preis ein Euro-Zeichen (€) enthält.

### Anpassungen
3. **QS-222**: Cockpit Icons - Fehlende Icons in den Cockpits wurden ergänzt und aktualisiert.
5. **QS-187**: Offline-Anzeigen - Anzeigen bei deaktivierter Onlinefunktion wurden optimiert.
6. Antwortfunktion - Die Antwortfunktion ist nur für ::ORA-Kunden aktiv. Für andere Nutzer wurde die Anzeige angepasst und die Funktion deaktiviert.

### Optimierungen
4. Gesamtbearbeitung Warnungseinstellungen - Das Anzeigeverhalten der Gesamtbearbeitung in den Warnungseinstellungen wurde verbessert, insbesondere beim Umschalten zwischen „Warnungen", „Anamnese" und „Alle" sowie bei der Nutzung der „Alles Ja/Nein"-Option.

## ::LEA

### Neues Produkt
1. **::LEA steht bereit** - Die Lizenzierung erfolgt automatisch, sobald die Einrichtung richtig abgeschlossen ist.

## Signexport.exe

### Optimierungen
1. Proxy-Konfiguration - Option hinzugefügt, um einen Proxy zu konfigurieren.

## MediaServerStarter

### Optimierungen
1. Dienst-Installation - Die Installation des MediaServerStarter als Dienst wurde verbessert. Ein Fehler, der zu unleserlichen Dienstnamen unter Windows führte, wurde behoben.
2. Dienstverwaltung - Der MediaServerStarter speichert Dienstnamen in der Base-Config, um Mehrfachinstallationen klar zuzuordnen.
   - Config-Parameter: `Server/mname` - Name des Dienstes vom MediaServer

## VDDS-stage1.exe

### Fehlerbehebungen
1. **QS-218**: Evident-Konfiguration - Behebung eines Fehlers, welcher die automatische Evident Konfiguration nicht richtig erkannt hat.

## Starter.exe

### Neue Funktionen
1. Selbstüberwachung - Der Starter.exe überwacht nun automatisch ihre Funktionsfähigkeit und startet sich bei Problemen selbstständig neu, um Unterbrechungen zu vermeiden.

### Optimierungen
2. Dienstverwaltung - Der Starter speichert Dienstnamen in der Base-Config, um Mehrfachinstallationen eindeutig zuordnen zu können.
   - Config-Parameter: `Server/bname` - Name des Dienstes der infoskop-Base
   - Config-Parameter: `Server/mname` - Name des Dienstes vom MediaServer
3. Fehlerprotokollierung - Der Starter protokolliert im Fehlerfall seine Versuche in `report.dat`, die Base zu erreichen. Diese Informationen werden auch in den Logcheck übernommen, um die Analyse zu erleichtern.
4. HL7-Server-Überwachung - HL7-Server werden nun automatisch überwacht. Beim Beenden des Base-Starters schließt der HL7-Server seinen Dienst „sanft", wodurch Netzwerkprobleme und lange Timeouts vermieden werden.

## HL7-Server

### Optimierungen
1. Socket-Server - Ermöglicht nun sanftes Schließen des Socket-Servers.

## Infoskop-Client.exe

### Neue Funktionen
1. ::LEA-Unterstützung - Unterstützung für ::LEA implementiert.

### Optimierungen
2. Webframe-Ladeanzeige - Bei längeren Ladezeiten der Webframes in infoskop-Monitor und ::LEA erhalten Nutzer nun eine „Bitte warten …"-Anzeige, die den Prozess transparent macht.

### Fehlerbehebungen
3. **QS-193**: Splash-Anzeigen - Ein Problem wurde behoben, bei dem in Z1 mehrere gleichartige Splash-Anzeigen gleichzeitig geladen werden konnten. Nun wird pro Ausführung nur noch eine Anzeige angezeigt.

## Updater und Full-Setup

### Anpassungen
1. Bonjour 32Bit entfernt - Die Installationsdatei für Bonjour 32Bit wurde entfernt. Das Produkt unterstützt ab sofort nur noch 64-Bit- und ARM-Systeme.
   - Es gibt nun eine zweite Installationsdatei für Bonjour 64Bit, die beide Architekturen (Intel und ARM) unterstützt.
   - Beide Installer können parallel und in beliebiger Reihenfolge installiert werden.
2. Dienst-Namensgebung - Bei Installationen mit mehreren Bases auf einem Rechner wird der Standard-Dienstname „infoskop-Base" nun nicht mehr automatisch vergeben, um Konflikte zu vermeiden.

### Optimierungen
3. Individuelle Dienstnamen - Der Updater kann nun individuelle Dienstnamen für Base und MediaServer übernehmen, um diese korrekt zu beenden und wieder zu starten.
   - Parameter: `/bname` (Base)
   - Parameter: `/mname` (MediaServer)

---
*Technische Dokumentation - Vollständige Änderungsübersicht für Entwicklung und IT-Administration*
