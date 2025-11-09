# infoskop-Base Update 5.0


Das neue Update 5.0 wird [TT.MM.JJJJ] veröffentlicht und im iMonitor zur Verfügung gestellt.

Wir arbeiten auf Hochtouren, auch den Newsletter, "What's New Screen" sowie Change Log für iMs im Portal bereitzustellen.

## Was gibt es Neues?

### ::LEA – Neues Produkt für Leistungserfassung

Mit infoskop::LEA steht ab sofort ein komplett neues Produkt zur Verfügung: die **Leistungserfassung**.

Die Lizenzierung für ::LEA erfolgt automatisch, sobald die Einrichtung korrekt abgeschlossen ist. Das neue Tool ist vollständig in den infoskop-Client integriert und ermöglicht eine vereinfachte Erfassung und Verwaltung von Leistungen direkt im System.

Bei längeren Ladezeiten der Webframes – etwa beim Öffnen des infoskop-Monitors oder ::LEA – erhalten Nutzer nun eine **„Bitte warten …"-Anzeige**, die den Prozess transparent macht und sicherstellt, dass das System aktiv arbeitet.

---

### Flexible Bildanpassung in E-Mails und Vorlagen

Die Arbeit mit Bildern in E-Mail- und Vorlagentexten wurde deutlich verbessert.

Anwender können nun **die Größe eingebetteter Bilder flexibel anpassen** – wahlweise per Drag & Drop, durch Auswahl voreingestellter Größen (50px, 75px, Originalgröße) oder durch Eingabe benutzerdefinierter Dimensionen.

Zusätzlich können **Links an Bildern einfach hinzugefügt, bearbeitet und entfernt werden**.

Dies ermöglicht eine deutlich bessere Gestaltung von E-Mail- und Vorlagentexten mit mehr Kontrolle über das Layout.

---

### Granulare Kontrolle bei der Löschung von Patientendaten

Der Ablauf der Löschung von Patientendaten im Monitor wurde **angepasst und optimiert**.

Beim Initiieren einer Löschung wird nun ein Dialog mit **feingranularer Kontrolle** angezeigt. Sie können jetzt genau auswählen, welche Datensubsets entfernt werden sollen:

- Dokumente
- Verlaufsdaten (History)
- Online-Daten

Zusätzlich kann ein **Datumslimit** („Nur Daten bis einschließlich") angegeben werden.

Da diese Aktion destruktiv ist, erfordert das System eine **doppelte Bestätigung** und warnt explizit, dass **gelöschte Daten nicht wiederhergestellt werden können**. Falls kein Datum angegeben wird, werden alle Daten bis heute gelöscht.

Dies bietet deutlich mehr Kontrolle und Sicherheit bei der Datenverwaltung – gezieltes Löschen statt pauschaler Entfernung.

---

### E-Mail-Icon mit Dropdown für schnellere Vorlagenauswahl

Für einen schnelleren Workflow wurde das **E-Mail-Icon mit einem Dropdown-Pfeil** ausgestattet.

Dadurch können Sie sofort eine Vorlage auswählen, bevor das Hauptfenster geöffnet wird. Diese Funktion ist verfügbar im:

- Patientenmenü
- Dokumentenbereich
- Auswertungs-Cockpits

So sparen Sie Zeit bei der E-Mail-Erstellung durch direkten Zugriff auf Ihre Vorlagen.

---

### Selbstüberwachung und automatischer Neustart für mehr Stabilität

Die **Starter.exe** wurde mit einer neuen Funktion ausgestattet: Sie **überwacht nun automatisch die Funktionsfähigkeit** der Base.

Falls der Hauptdienst nicht mehr reagiert – beispielsweise während der Verarbeitung eines sehr großen Dokuments – startet der Starter den Dienst **selbstständig neu**.

Das Timeout erhöht sich automatisch bei wiederholten Neustarts, sodass auch langwierige Aktionen eine Chance auf erfolgreichen Abschluss haben. Diese Funktion vermeidet Unterbrechungen und verhindert System-Hänger, wodurch manuelle Neustarts überflüssig werden.

**Mehr Stabilität, weniger manuelle Eingriffe – das System heilt sich selbst.**

---

## Was gibt's sonst noch?

### Korrekte E-Mail-Statusmeldungen

Ein wichtiger Fehler wurde behoben: E-Mails werden nicht mehr fälschlicherweise als „erfolgreich versendet" angezeigt, wenn die **SMTP-Serverdaten fehlerhaft oder leer** sind.

Sie erhalten jetzt keine falschen Erfolgsmeldungen mehr und haben volle Transparenz über den tatsächlichen Versandstatus.

---

### Links in E-Mails und Vorlagen öffnen sich jetzt korrekt

Ein lange bestehendes Problem wurde gelöst: Links in E-Mail-Texten, Vorlagentexten sowie im **Formularlinkbaukasten** öffnen sich nun **im lokalen Browser**.

Im Formularlinkbaukasten wurde das Verhalten leicht angepasst – Links müssen nun direkt angeklickt werden, um eine Vorschau zu erhalten.

---

### Konsistente Deaktivierung der Onlinefunktion

Die Anzeigen und das Verhalten bei deaktivierter Onlinefunktion wurden optimiert.

**Vorher:** Obwohl Onlinefunktionen deaktiviert waren, blieben bestimmte Menüeinträge zugänglich, und E-Mails konnten noch aus der Patientenakte oder über Hintergrundprozesse versendet werden.

**Jetzt:** Bei deaktivierter Onlinefunktion sind **alle zugehörigen Menüeinträge und E-Mail-Icons** in der gesamten Anwendung (einschließlich Patientenakte und Cockpits) **gesperrt, deaktiviert und ausgegraut**.

Dies sorgt für eine klare, systemweite Durchsetzung der Deaktivierung – keine unerwarteten Funktionen mehr.

---

### ::ORA-Antwortfunktion nur für lizenzierte Kunden

Die Lizenzabfrage für die **::ORA-Antwortfunktion** wurde behoben.

Die Funktion ist jetzt nur für ::ORA-Kunden aktiv. Für alle anderen Nutzer wurde die Anzeige angepasst und die Funktion deaktiviert – keine Verwirrung mehr durch Funktionen, die Sie nicht nutzen können.

---

### Preisübernahme in Cockpits funktioniert mit Euro-Symbol

Ein Fehler wurde behoben, durch den die Preisübernahme im **PA-Cockpit und Bleaching-Cockpit** nicht korrekt funktionierte, wenn der Preis ein **Euro-Zeichen (€)** enthielt.

Die Preisübernahme läuft nun zuverlässig – unabhängig vom Vorhandensein des €-Symbols.

---

### Vollständige Icons in den Cockpits

Fehlende Icons im PA-Cockpit und Bleaching-Cockpit wurden **ergänzt und aktualisiert**, sodass nun eine vollständige visuelle Darstellung für bessere Orientierung zur Verfügung steht.

---

### HL7-Server: Sanftes Schließen verhindert Netzwerkprobleme

HL7-Server werden nun **automatisch überwacht**. Beim Beenden des Base-Starters schließt der HL7-Server seinen Dienst **„sanft"**.

Dies verhindert Netzwerkprobleme und lange Timeouts, die zuvor auftraten, wenn der Server sich nicht ordnungsgemäß schloss.

Das Ergebnis: **Stabilere HL7-Verbindungen ohne Wartezeiten und Verbindungsprobleme.**

---

### 64-Bit und ARM-Unterstützung – Bonjour 32-Bit entfernt

Um Performance und aktuelle Standards sicherzustellen, wurde die **Installationsdatei für Bonjour 32-Bit entfernt**.

Das Produkt unterstützt ab sofort **nur noch 64-Bit- und ARM-Systeme**.

Es gibt nun eine zweite 64-Bit Bonjour-Installationsdatei, die sowohl Intel- als auch ARM-Architekturen unterstützt. Beide Installer können parallel in beliebiger Reihenfolge installiert werden.

---

### Verbesserte Updater-Dienstverwaltung bei Mehrfachinstallationen

Für Kunden mit **mehreren Standorten** ist es möglich und sinnvoll, auf einem Server mehrere Base-Instanzen zu installieren.

Bei Installationen mit mehreren Bases auf einem Rechner wird der Standard-Dienstname **„infoskop-Base"** nun **nicht mehr automatisch vergeben**, um Konflikte zu vermeiden.

Der Updater kann nun **individuelle Dienstnamen** für Base (`/bname`) und MediaServer (`/mname`) übernehmen, um diese korrekt zu beenden und wieder zu starten.

Dies ermöglicht eine konfliktfreie Installation mehrerer Base-Instanzen auf einem Rechner.

---

## Anpassungen und Bug-Fixes

Es wurden Anpassungen/Fixes vorgenommen für:

**infoskop-Base.exe**
- Behebung eines Fehlers, wodurch E-Mails scheinbar erfolgreich versendet werden konnten, obwohl fehlerhafte Daten für den SMTP-Server hinterlegt waren (QS-227)

**infoskop-Monitor**
- Option hinzugefügt, durch die man nun die Größe von embedded Bildern in Mail- oder Vorlagentexten anpassen kann
- Der Ablauf der Löschung von Patientendaten im Monitor wurde angepasst und optimiert
- Behebung eines Fehlers, durch den es nicht möglich war, Links in Mail- oder Vorlagentexten sowie im Formularlinkbaukasten im lokalen Browser zu öffnen (QS-177)
- Fehlende Icons für die Cockpits aktualisiert (QS-222)
- Die Funktionsweise der Gesamtbearbeitung in den Warnungseinstellungen wurde optimiert
- Die Anzeigen bei deaktivierter Onlinefunktion wurden angepasst (QS-187)
- Lizenzabfrage der infoskop::ORA-Funktion behoben (INFO-1194)
- Preisübernahme in PA- und Bleaching-Cockpit funktioniert nun auch mit Euro-Zeichen (QS-97)

**infoskop::LEA**
- Einbindung des neuen Webframes für den Client
- Funktionen in der Base zur Verwaltung der Anfragen und Datenhaltung
- Automatische Aktivierung der Lizenz bei korrekt hinterlegtem Leistungskatalog

**Signexport.exe**
- Option hinzugefügt, um einen Proxy zu konfigurieren

**MediaServerStarter**
- Optimierungen für die Installation als Dienst, behebt einen Fehler, bei dem installierte Dienstnamen korrupt und nicht für Windows leserlich waren (INFO-1157)
- Der MediaServerStarter schreibt jetzt informativ seinen Dienstnamen in die Base-config bei abweichenden Installationsnamen

**VDDS-stage1.exe**
- Behebung eines Fehlers, welcher die automatische Evident-Konfiguration nicht richtig erkannt hat (QS-218)

**Starter.exe**
- Option hinzugefügt, die automatisch die Funktionalität des TCP-Socketservers der infoskop-Base.exe überwacht und nach einem Timeout einen Neustart der Anwendung auslöst (INFO-1187)
- Der Starter schreibt jetzt informativ seine Dienstnamen in die Base-config bei abweichenden Installationsnamen
- Der Starter dokumentiert seine Versuche, die Base zu erreichen im Fehlerfall in der report.dat. Der Inhalt wird auch in den Logcheck übertragen
- Optimierungen für die Installation als Dienst, behebt einen Fehler, bei dem installierte Dienstnamen korrupt und nicht für Windows leserlich waren (INFO-1156)
- Automatisches Überwachen von HL7-Servern. Ermöglicht „sanftes Beenden" des HL7-Servers, wenn der Base-Starter beendet wird

**HL7-Server**
- Ermöglicht nun sanftes Schließen des Socket-Servers

**infoskop-Client.exe**
- Unterstützung für infoskop::LEA
- Für die verzögerte Anzeige der Webframes (infoskop-Monitor und infoskop::LEA) wurde eine „Bitte warten …" Anzeige bereitgestellt (INFO-1196)
- Behebung eines Fehlers, wodurch es sein konnte, dass bei Z1 zu viele gleichartige Splash-Anzeigen geladen wurden. Nur noch eine Anzeige pro Ausführung ist möglich (QS-193)

**infoskop-Base-Updater und infoskop-Base-Setup**
- Die Installationsdatei für Bonjour 32bit wurde entfernt. Das Produkt unterstützt ab sofort nur noch 64-Bit- und ARM-Systeme (INFO-1188)
- Es gibt nun eine zweite Installationsdatei für Bonjour 64bit, die beide Architekturen (Intel und ARM) unterstützt
- Der Dienst Default-Name „infoskop-Base" wird jetzt nur noch angenommen, wenn dem Updater NICHT das /MULTIPLEBASES Flag mitgegeben wurde
- Dem Updater können jetzt über /bname (Base) und /mname (MediaServer) die Dienst-Namen mitgegeben werden
