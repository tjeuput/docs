# Release Notes Base 5.0.0 - TECHNIK
## Vorläufige Version (Interner Gebrauch)

## infoskop-Base.exe

### Fehlerbehebungen
1. **QS-227**: E-Mail-Versandstatus - Korrektur eines kritischen Fehlers, bei dem E-Mails trotz leerer oder fehlerhafter SMTP-Serverdaten fälschlicherweise als erfolgreich versendet markiert wurden. Das System meldet nun korrekt Versandfehler.

## infoskop-Monitor

### Neue Funktionen
1. Flexible Bildgrößenanpassung - Implementierung einer Funktion zur dynamischen Anpassung der Größe eingebetteter Bilder in E-Mail- und Vorlagentexten für verbesserte Inhaltsgestaltung.

### Fehlerbehebungen
2. **QS-177**: Link-Handling - Behebung eines Problems, das verhinderte, dass Links in E-Mail- und Vorlagentexten sowie im Formularlinkbaukasten im lokalen Browser geöffnet werden konnten. Zusätzlich wurde die Benutzerinteraktion im Formularlinkbaukasten modifiziert: Links erfordern nun einen direkten Klick für die Vorschaufunktion.

7. **QS-97**: Preisübernahme-Logik - Korrektur der Preisübernahmefunktion in PA- und Bleaching-Cockpit. Das System verarbeitet nun korrekt Preise mit Euro-Zeichen (€).

### Anpassungen
3. **QS-222**: Cockpit-Iconographie - Aktualisierung und Ergänzung fehlender Icons in den Cockpit-Oberflächen für verbesserte Benutzerführung.

5. **QS-187**: Offline-Funktionalität - Optimierung der Anzeigelogik bei deaktivierter Onlinefunktion.

6. Antwortfunktion - Implementierung einer lizenzbezogenen Feature-Steuerung: Die Antwortfunktion ist ausschließlich für ::ORA-Kunden verfügbar. Für Nicht-::ORA-Nutzer wurde die UI entsprechend angepasst und die Funktion deaktiviert.

### Optimierungen
4. Warnungseinstellungen - Gesamtbearbeitung - Verbesserung des Anzeigeverhaltens der Gesamtbearbeitungsfunktion in den Warnungseinstellungen. Betrifft insbesondere den Wechsel zwischen den Modi „Warnungen", „Anamnese" und „Alle" sowie die Funktionalität der „Alles Ja/Nein"-Option.

## ::LEA

### Neues Produkt
1. **::LEA Produkteinführung** - Das neue Produkt ::LEA steht zur Verfügung. Die Lizenzaktivierung erfolgt automatisch nach erfolgreichem Abschluss der Einrichtungsprozedur.

## Signexport.exe

### Optimierungen
1. Proxy-Unterstützung - Implementierung einer Konfigurationsoption für Proxy-Server-Einstellungen zur Unterstützung von Netzwerkumgebungen mit Proxy-Anforderungen.

## MediaServerStarter

### Optimierungen
1. Dienst-Installation - Verbesserung der Dienstinstallationsroutine. Behebung eines Fehlers, der unter Windows zu unleserlichen bzw. fehlerhaften Dienstnamen führte.

2. Dienstverwaltung - Der MediaServerStarter persistiert nun Dienstnamen in der Base-Konfiguration zur eindeutigen Identifizierung bei Mehrfachinstallationen.
   - Config-Parameter: `Server/mname` - Speichert den Namen des MediaServer-Dienstes

## VDDS-stage1.exe

### Fehlerbehebungen
1. **QS-218**: Evident-Integrationserkennung - Korrektur eines Fehlers in der automatischen Evident-Konfigurationserkennung. Das System identifiziert nun korrekt vorhandene Evident-Konfigurationen.

## Starter.exe

### Neue Funktionen
1. Selbstüberwachungsmechanismus - Implementierung eines automatischen Watchdog-Systems: Der Starter.exe überwacht kontinuierlich die eigene Funktionsfähigkeit und führt bei Problemen automatisch einen Neustart durch, um Betriebsunterbrechungen zu minimieren.

### Optimierungen
2. Dienstverwaltung - Persistierung von Dienstnamen in der Base-Konfiguration zur eindeutigen Zuordnung bei Mehrfachinstallationen.
   - Config-Parameter: `Server/bname` - Speichert den Namen des infoskop-Base-Dienstes
   - Config-Parameter: `Server/mname` - Speichert den Namen des MediaServer-Dienstes

3. Fehlerprotokollierung - Erweitertes Logging-System: Im Fehlerfall protokolliert der Starter alle Verbindungsversuche zur Base in der Datei `report.dat`. Diese Informationen werden automatisch in den Logcheck integriert zur vereinfachten Fehleranalyse.

4. HL7-Server-Überwachung - Implementierung einer automatischen Überwachung für HL7-Server. Beim Herunterfahren des Base-Starters wird der HL7-Server-Dienst nun kontrolliert beendet (graceful shutdown), wodurch Netzwerkprobleme und lange Timeout-Perioden vermieden werden.

## HL7-Server

### Optimierungen
1. Socket-Server-Verwaltung - Implementierung eines graceful shutdown-Mechanismus für den Socket-Server zur Vermeidung von Verbindungsproblemen beim Beenden.

## Infoskop-Client.exe

### Neue Funktionen
1. ::LEA-Integration - Vollständige Implementierung der ::LEA-Unterstützung im Client.

### Optimierungen
2. Webframe-Ladeanzeige - Implementierung einer „Bitte warten …"-Anzeige für längere Ladezeiten der Webframes in infoskop-Monitor und ::LEA zur Verbesserung der User Experience und Transparenz des Ladeprozesses.

### Fehlerbehebungen
3. **QS-193**: Splash-Screen-Verwaltung - Behebung eines Problems in Z1, bei dem mehrere identische Splash-Anzeigen gleichzeitig geladen werden konnten. Das System zeigt nun pro Ausführung nur noch eine einzelne Anzeige.

## Updater und Full-Setup

### Anpassungen
1. Bonjour 32Bit entfernt - **Breaking Change**: Die 32-Bit-Installationsdatei für Bonjour wurde aus dem Installer entfernt. Das Produkt unterstützt ab Version 5.0.0 ausschließlich 64-Bit- und ARM-Systeme.
   - Eine neue Bonjour 64Bit-Installationsdatei unterstützt beide Architekturen (Intel x64 und ARM64)
   - Beide Installer sind kompatibel und können in beliebiger Reihenfolge parallel installiert werden

2. Dienst-Namensgebung - Änderung im Installationsverhalten: Bei Mehrfach-Installationen (mehrere Bases auf einem System) wird der Standard-Dienstname „infoskop-Base" nicht mehr automatisch vergeben, um Namenskonflikte zu vermeiden.

### Optimierungen
3. Individuelle Dienstnamen - Der Updater unterstützt nun individuelle Dienstnamen für Base und MediaServer zur korrekten Steuerung (Beenden/Starten) spezifischer Dienste.
   - Kommandozeilenparameter: `/bname` (für Base-Dienst)
   - Kommandozeilenparameter: `/mname` (für MediaServer-Dienst)

---
*Technische Dokumentation - Vollständige Änderungsübersicht für Entwicklung und IT-Administration*
*Basiert auf vorläufigen Release Notes - Stand: Interner Review*
