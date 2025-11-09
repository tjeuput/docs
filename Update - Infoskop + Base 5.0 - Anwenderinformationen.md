# Update: Infoskop + Base 5.0 – Was ist neu, was ist verbessert?

**Für Anwender und Kunden: Die wichtigsten Neuerungen und Verbesserungen im Überblick**

---

## 🆕 Neue Funktionen

### 1. **::LEA – Neues Produkt für Leistungserfassung**

**Was ist neu:**
- Infoskop::LEA steht ab sofort zur Verfügung
- Die Lizenzierung erfolgt automatisch bei korrekter Einrichtung
- Vollständige Integration in den Infoskop-Client

**Nutzen für Sie:**
Vereinfachte Erfassung und Verwaltung von Leistungen direkt im System.

[missing: no previous state mentioned]

---

### 2. **Flexible Bildanpassung in E-Mails und Vorlagen**

**Was ist neu:**
- Anwender können nun die Größe eingebetteter Bilder flexibel anpassen
- Anpassung per Drag & Drop möglich
- Voreingestellte Größen (50px, 75px, Originalgröße) verfügbar
- Benutzerdefinierte Dimensionen einstellbar
- Links an Bildern können einfach hinzugefügt, bearbeitet und entfernt werden

**Nutzen für Sie:**
Bessere Gestaltung von E-Mail- und Vorlagentexten mit mehr Kontrolle über das Layout.

[missing: no previous state mentioned]

---

### 3. **Selbstüberwachung und automatischer Neustart (Starter.exe)**

**Was ist neu:**
- Der Starter.exe überwacht automatisch die Funktionsfähigkeit der Base
- Bei Unresponsiveness wird der Service automatisch neu gestartet
- Das Timeout erhöht sich automatisch bei wiederholten Neustarts, um langwierigen Aktionen Zeit zum Abschluss zu geben
- Verhindert System-Hänger bei der Verarbeitung großer Dokumente

**Nutzen für Sie:**
Mehr Stabilität und weniger manuelle Eingriffe – das System heilt sich selbst.

**Vorher:**
[missing: no previous state mentioned – system required manual restart when Base became unresponsive]

---

### 4. **E-Mail-Icon mit Dropdown für schnellere Vorlagenauswahl**

**Was ist neu:**
- Das E-Mail-Icon verfügt nun über einen Dropdown-Pfeil
- Sofortige Auswahl einer Vorlage möglich, bevor das Hauptfenster geöffnet wird
- Verfügbar im Patientenmenü, in Dokumenten und in den Auswertungs-Cockpits

**Nutzen für Sie:**
Schnellerer Workflow bei der E-Mail-Erstellung durch direkten Zugriff auf Vorlagen.

[missing: no previous state mentioned]

---

### 5. **Granulare Kontrolle bei der Löschung von Patientendaten**

**Was ist neu:**
- Neuer Dialog mit feingranularer Kontrolle beim Löschen von Patientendaten
- Auswahl, welche Datensubsets gelöscht werden sollen:
  - Dokumente
  - Verlaufsdaten (History)
  - Online-Daten
- Möglichkeit zur Angabe eines Datumslimits („Nur Daten bis einschließlich")
- Doppelte Bestätigung erforderlich
- Warnung, dass gelöschte Daten nicht wiederhergestellt werden können

**Nutzen für Sie:**
Mehr Kontrolle und Sicherheit bei der Datenverwaltung, gezieltes Löschen statt pauschaler Entfernung.

**Vorher:**
[missing: no previous state mentioned – likely all patient data was deleted without granular selection]

---

### 6. **"Bitte warten…"-Anzeige bei längeren Ladezeiten**

**Was ist neu:**
- Bei längeren Ladezeiten (z.B. beim Öffnen von infoskop-Monitor oder ::LEA) erscheint eine „Bitte warten…"-Anzeige
- Macht den Ladeprozess transparent

**Nutzen für Sie:**
Klarheit darüber, dass das System aktiv arbeitet – keine Unsicherheit mehr bei längeren Ladezeiten.

**Vorher:**
[missing: no previous state mentioned – likely no loading indicator was shown]

---

## ✅ Verbesserungen und Fehlerbehebungen

### 7. **Korrekte E-Mail-Statusmeldungen**

**Was wurde verbessert:**
- E-Mails werden nicht mehr fälschlicherweise als „erfolgreich versendet" angezeigt, wenn die SMTP-Serverdaten fehlerhaft oder leer sind
- Zuverlässigere Statusbenachrichtigungen

**Nutzen für Sie:**
Sie erhalten keine falschen Erfolgsmeldungen mehr – Transparenz über den tatsächlichen Versandstatus.

**Vorher:**
System zeigte E-Mails als erfolgreich versendet an, selbst wenn SMTP-Server-Konfiguration fehlerhaft war (QS-227).

---

### 8. **Links in E-Mails und Vorlagen öffnen sich jetzt korrekt**

**Was wurde verbessert:**
- Links in E-Mail-Texten, Vorlagentexten und im Formularlinkbaukasten öffnen sich nun im lokalen Browser
- Im Formularlinkbaukasten muss der Link direkt angeklickt werden für eine Vorschau (kleine Verhaltensanpassung)

**Nutzen für Sie:**
Reibungslose Navigation zu verlinkten Inhalten ohne Fehlverhalten.

**Vorher:**
Links konnten nicht im lokalen Browser geöffnet werden – Funktion war blockiert (QS-177).

---

### 9. **Preisübernahme in Cockpits funktioniert mit Euro-Symbol**

**Was wurde verbessert:**
- Preisübernahme im PA-Cockpit und Bleaching-Cockpit funktioniert nun korrekt, auch wenn der Preis ein Euro-Zeichen (€) enthält

**Nutzen für Sie:**
Zuverlässige Preisübernahme ohne manuelle Korrekturen.

**Vorher:**
Preisübernahme funktionierte nicht, wenn das Euro-Symbol (€) im Preis enthalten war (QS-97).

---

### 10. **Vollständige Icons in den Cockpits**

**Was wurde verbessert:**
- Fehlende Icons im PA-Cockpit und Bleaching-Cockpit wurden ergänzt und aktualisiert

**Nutzen für Sie:**
Vollständige visuelle Darstellung für bessere Orientierung.

**Vorher:**
Icons waren im Auswertungsbereich der Cockpits unvollständig (QS-222).

---

### 11. **Optimierte Gesamtbearbeitung in Warnungseinstellungen**

**Was wurde verbessert:**
- Verbessertes Anzeigeverhalten beim Umschalten zwischen „Warnungen", „Anamnese" und „Alle"
- Optimierte Nutzung der „Alles Ja/Nein"-Option

**Nutzen für Sie:**
Flüssigere Bearbeitung von Einstellungen, besonders bei Massenänderungen.

**Vorher:**
[missing: no previous state mentioned – likely display behavior was inconsistent during bulk edits]

---

### 12. **Konsistente Deaktivierung der Onlinefunktion**

**Was wurde verbessert:**
- Bei deaktivierter Onlinefunktion sind nun alle zugehörigen Menüeinträge und E-Mail-Icons gesperrt, deaktiviert und ausgegraut
- Gilt für die gesamte Anwendung, einschließlich Patientenakte und Cockpits
- Keine E-Mails mehr aus der Patientenakte oder über Hintergrundprozesse, wenn Onlinefunktion deaktiviert ist

**Nutzen für Sie:**
Klare, systemweite Durchsetzung der Deaktivierung – keine unerwarteten Funktionen mehr.

**Vorher:**
Obwohl Onlinefunktionen deaktiviert waren, blieben bestimmte Menüeinträge zugänglich und E-Mails konnten noch versendet werden (QS-187).

---

### 13. **::ORA-Antwortfunktion nur für lizenzierte Kunden**

**Was wurde verbessert:**
- Lizenzabfrage für ::ORA-Antwortfunktion behoben
- Funktion ist nur für ::ORA-Kunden aktiv
- Für andere Nutzer wurde die Anzeige angepasst und die Funktion deaktiviert

**Nutzen für Sie:**
Keine Verwirrung durch Funktionen, die Sie nicht nutzen können.

**Vorher:**
::ORA-Lizenzabfrage funktionierte nicht korrekt, Funktion wurde auch Nicht-::ORA-Kunden angezeigt (INFO-1194).

---

### 14. **Automatische Evident-Konfiguration (VDDS-stage1.exe)**

**Was wurde verbessert:**
- Erweiterte Schnittstelle mit Evident Version 6 erkennt und konfiguriert sich nun automatisch korrekt

**Nutzen für Sie:**
Keine technische Supportintervention mehr erforderlich für die Konfiguration der Partnerverbindung.

**Vorher:**
Automatische Evident-Konfiguration wurde nicht korrekt erkannt, manuelle Konfiguration durch Support notwendig (QS-218).

---

## 🔧 Technische Verbesserungen und Stabilität

### 15. **HL7-Server: Sanftes Schließen verhindert Netzwerkprobleme**

**Was wurde verbessert:**
- HL7-Server werden automatisch überwacht
- Beim Beenden des Base-Starters schließt der HL7-Server seinen Dienst „sanft"
- Verhindert Netzwerkfehler und lange Timeouts

**Nutzen für Sie:**
Stabilere HL7-Verbindungen ohne Wartezeiten und Verbindungsprobleme.

**Vorher:**
HL7-Server schloss sich nicht ordnungsgemäß, was zu Netzwerkfehlern mit langen Timeouts führte.

---

### 16. **Verbesserte Logging-Funktionen (Starter.exe)**

**Was wurde verbessert:**
- Starter protokolliert seine Versuche, die Base zu erreichen, im Fehlerfall in der report.dat
- Informationen werden in den Logcheck übertragen

**Nutzen für Sie:**
Einfachere Fehleranalyse und schnellere Problemlösung durch bessere Protokollierung.

**Vorher:**
[missing: no previous state mentioned – likely no detailed logging of Base connection attempts]

---

### 17. **Proxy-Konfiguration für Signexport.exe**

**Was wurde verbessert:**
- Option hinzugefügt, um einen Proxy zu konfigurieren

**Nutzen für Sie:**
Flexiblere Netzwerkkonfiguration in Umgebungen mit Proxy-Servern.

**Vorher:**
[missing: no previous state mentioned – likely no proxy configuration was possible]

---

### 18. **Optimierte Dienst-Installation (MediaServerStarter)**

**Was wurde verbessert:**
- Fehler behoben, der zu unleserlichen Dienstnamen unter Windows führte
- MediaServerStarter speichert Dienstnamen in der Base-Config für eindeutige Zuordnung bei Mehrfachinstallationen

**Nutzen für Sie:**
Klarere Systemverwaltung, besonders bei komplexeren Installationen.

**Vorher:**
Installierte Dienstnamen waren korrupt und nicht für Windows leserlich (INFO-1157).

---

### 19. **Optimierte Dienst-Installation (Starter.exe)**

**Was wurde verbessert:**
- Fehler behoben, der zu unleserlichen Dienstnamen unter Windows führte
- Starter speichert Dienstnamen in der Base-Config (Server/bname, Server/mname) für eindeutige Zuordnung

**Nutzen für Sie:**
Stabilere Installation und bessere Verwaltbarkeit bei mehreren Base-Instanzen.

**Vorher:**
Installierte Dienstnamen waren korrupt und nicht für Windows leserlich (INFO-1156).

---

### 20. **Nur noch eine Splash-Anzeige pro Ausführung**

**Was wurde verbessert:**
- Problem behoben, bei dem in Z1 mehrere gleichartige Splash-Anzeigen gleichzeitig geladen werden konnten
- Nur noch eine Anzeige pro Ausführung

**Nutzen für Sie:**
Aufgeräumtere Benutzeroberfläche beim Systemstart.

**Vorher:**
Mehrere identische Update-Screens (Splash Screens) konnten gleichzeitig erscheinen (QS-193).

---

## 🖥️ System- und Installationsanpassungen

### 21. **64-Bit und ARM-Unterstützung – Bonjour 32-Bit entfernt**

**Was wurde geändert:**
- Installationsdatei für Bonjour 32-Bit wurde entfernt
- Produkt unterstützt ab sofort nur noch 64-Bit- und ARM-Systeme
- Zweite 64-Bit Bonjour-Installationsdatei verfügbar, die sowohl Intel- als auch ARM-Architekturen unterstützt
- Beide Installer können parallel in beliebiger Reihenfolge installiert werden

**Nutzen für Sie:**
Modernere Systemunterstützung und bessere Performance auf aktuellen Systemen.

**Vorher:**
32-Bit Bonjour wurde unterstützt (INFO-1188).

---

### 22. **Verbesserte Updater-Dienstverwaltung bei Mehrfachinstallationen**

**Was wurde geändert:**
- Standard-Dienstname „infoskop-Base" wird bei Mehrfachinstallationen nicht mehr automatisch vergeben
- Updater kann individuelle Dienstnamen für Base (/bname) und MediaServer (/mname) übernehmen
- Korrekte Beendigung und Neustart von Diensten mit abweichenden Namen

**Nutzen für Sie:**
Konfliktfreie Installation mehrerer Base-Instanzen auf einem Rechner.

**Vorher:**
[missing: no previous state mentioned – likely conflicts occurred with multiple Base installations using the same default service name]

---

## 📋 Zusammenfassung

**Infoskop Base 5.0** bringt bedeutende Verbesserungen in drei Hauptbereichen:

1. **Neue Funktionen**: ::LEA-Integration, flexible Bildbearbeitung, selbstheilendes System
2. **Verbesserte Zuverlässigkeit**: Korrekte E-Mail-Statusmeldungen, funktionierende Links, konsistente Deaktivierung von Funktionen
3. **Erhöhte Stabilität**: Automatische Überwachung, sanftes Schließen von Servern, verbesserte Protokollierung

Das Update konzentriert sich auf Effizienz, Kontrolle und Verlässlichkeit – für einen reibungsloseren Arbeitsalltag.

---

**Stand:** November 2025
**Version:** Infoskop Base 5.0.0
**Quelle:** Vorläufige Release Notes (interner Gebrauch)
