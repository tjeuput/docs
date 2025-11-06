Infoskop-Base Version 5.0.0

Infoskop-Base.exe

-              Behebung eines Fehlers, wodurch E-Mails scheinbar erfolgreich versendet werden konnten, obwohl fehlerhafte Daten für den SMTP-Server hinterlegt waren. (INFO-1243)

Infoskop-Monitor

-              Option hinzugefügt, durch die man nun die Größe von embedded Bildern in Mail- oder Vorlagentexten anpassen kann. [[WYSIWYG-Editor (CK5-Editor in IM) die Funktion erweitert, Bilder per Drag & Drop hinzuzufügen]]

-              Der Ablauf der Löschung von Patientendaten im Monitor wurde angepasst und optimiert. (AZUBI-401)

-              Es wurde ein Fehler behoben, durch den es nicht möglich war Links in Mail- oder Vorlagentexten, sowie im Formularlinkbaukasten im lokalen Browser zu öffnen. ([[Base Updater 4 - IM – Link generieren – Link-Tag auf der ganze Vorschaufläche| IM – Link generieren – Link-Tag auf der ganze Vorschaufläche]], [Base 4.2.0_Unerwünschter Linkverhalten im neuen CKEditor 5 bei E-Mail-Vorlagen]())

-              Es wurden fehlende Icons für die Cockpits aktualisiert. ([IM - fehlende Icons in Auswertungsbreich]()

-              Die Funktionsweise der Gesamtbearbeitung in den Warnungseinstellungen wurde optimiert. ([AZUBI-399](AZUBI-399))

-              Es wurden die Anzeigen bei deaktivierter Onlinefunktion angepasst. ([AZUBI-403](IM Zugriff auf Onlineformular-Einstellungen möglich, obwohl Onlineformulare deaktiviert sind), AZUBI-421)

-              Es wurde ein Fehler bei der Abfrage der infoskop::ORA-Lizenz behoben (INFO-1194)

Infoskop::LEA

-              Einbindung des neuen Webframes für den Client

-              Funktionen in der Base zur Verwaltung der Anfragen und Datenhaltung

-              Automatische Aktivierung der Lizenz bei korrekt hinterlegtem Leistungskatalog

Signexport.exe

-              Option hinzugefügt, um einen Proxy zu konfigurieren

MediaServerStarter

-              Optimierungen für die Installation als Dienst, behebt einen Fehler, bei dem installierte Dienstnamen korrupt und nicht für Windows leserlich waren (INFO-1157)

-              Der MediaServerStarter schreibt jetzt informativ und für spätere Versionen seinen Dienstnamen in die Base-config, sofern diese einen abweichenden Installationsnamen haben, wie zB. Bei mehreren MediaServern auf einem Rechner der Fall:

o   Server/mname    Name des Dienstes vom MediaServer

VDDS-stage1.exe

-              Behebung eines Fehlers, welcher die automatische Evident Konfiguration nicht richtig erkannt hat. (INFO-1190)

Starter.exe

-              Option hinzugefügt, die automatisch die Funktionalität des TCP-Socketserver der infoskop-Base.exe überwacht und nach einem Timeout einen Neustart der Anwendung auslöst. (Default an; abschaltbar) – der Timeout erhöht sich automatisch wenn er eintritt und ermöglicht so einem Nutzer, bei wiederholtem Versuchen mit einer langwierigen Aktion doch noch Erfolg zu haben (INFO-1187)  
Flags – Base-config und Standardwerte:

o   server/restartWhenUnresponsive=1    Wenn auf 0 gestellt wird die Base nicht mehr automatisch neu gestartet, wenn der Base Socket-Server ausfällt

o   server/lifesignToBaseInterval=5000    Intervall, in dem der Starter den Socket Server der infoskop-Base prüft (Angabe in ms)

o   server/lifesignRestartBusyBaseAfterInterval=30000   Zeit, die der infoskop-Base Socket Server nicht erreichbar sein darf, bevor er neu gestartet wird. Dieser Wert erhöht sich automatisch jedes Mal, wenn die Base beendet wird, falls ein Kunde eine langwierige Aufgabe immer wieder versucht, um dieser eine Chance auf Erfolg zu geben – Reset beim Neustart (Angabe in ms)  
  

-              Der Starter schreibt jetzt informativ und für spätere Versionen seine Dienstnamen in die Base-config, sofern diese einen abweichenden Installationsnamen haben, wie zB. Bei mehreren Bases auf einem Rechner der Fall:

o   Server/bname    Name des Dienstes der infoskop-Base

o   Server/mname    Name des Dienstes vom MediaServer

-              Der Starter dokumentiert seine Versuche, die Base zu erreichen im Fehlerfall in der report.dat. Der Inhalt davon wird auch in den Logcheck übertragen. (INFO-1187)

-              Optimierungen für die Installation als Dienst, behebt einen Fehler, bei dem installierte Dienstnamen korrupt und nicht für Windows leserlich waren (INFO-1156)

-              Automatisches Überwachen von HL7 Servern (unabhängig von der AppToStart Mechanik). Ermöglicht „sanftes Beenden“ des HL7 Servers, wenn der Base-Starter beendet wird, so dass der HL7-Server ordnungsgemäß seinen Socket Server schließen kann, bevor er sich selbst beendet. Dies behebt einen Netzwerkfehler mit langen Timeouts bei manchen Kunden.  
Achtung: Sanftes Schließen benötigt beim Hl7-Server in der config das server/ useChilkatSockets Flag!  
Flags – Base-config und Standardwerte:

o   hl7/smartHandling=0    Wenn auf 1 gestellt wird der HL7-Server automatisch überwacht und sanft beendet (vorher Einträge aus AppToStart entfernen)  
Achtung: Benötigt hl7/enabled=1

o   hl7/waitforclose=6000    Zeit, die der Starter auf das sanfte Beenden des HL7-Servers wartet, bevor dieser doch hart geschlossen wird. Mit 0 deaktivierbar (Angabe in ms)

HL/-Server

-              Ermöglicht nun sanftes Schließen des Socket-Servers (Details: Siehe beim Starter)  
Flags – Hl7-Server config und Standardwerte:

o   server/useChilkatSockets=0   Wechsel von den alten Sockets auf eine neuere Art Sockets mit mehr Möglichkeiten – Voraussetzung für das sanfte Schließen. Wird automatisch aktiviert, wenn module/orbis=1 und server/openstream=1

Infoskop-Client.exe

-              Unterstützung für infoskop::LEA

o   Aufruf der Windows Applikation als eigenständige Windowsfensterinstanz der Anwendung

o   Abfragen der Lizenz bei der infoskop-Base.exe

-              Für die verzögerte Anzeige der Webframes (infoskop-Monitor und infoskop::LEA) wurde eine „Bitte warten …“ Anzeige bereitgestellt (INFO-1196)

-              Behebung eines Fehlers, wodurch es sein konnte, dass bei Z1 zu viele gleichartige Splash Anzeigen geladen wurden. Nur noch eine Anzeige pro Ausführung ist möglich. (INFO-1192)

Infoskop-Base-Updater und infoskop-Base-Setup

-              Die Installationsdatei für Bonjour 32bit wurde entfernt. (INFO-1188)

-              Es gibt nun eine zweite Installationsdatei für Bonjour 64bit gleicher Version, aber im Praxistest funktionierte immer nur einer der Installer, wahrscheinlich abhängig von der Architektur (ARM und Intel Chips). Beide können gefahrlos in beliebiger Reihenfolge parallel installiert werden. (INFO-1188)

-              Der Dienst Default-Name „infoskop-Base“ wird jetzt nur noch angenommen, wenn dem Updater NICHT das /MULTIPLEBASES Flag mitgegeben wurde (für Installationen mit mehreren Bases auf einem Rechner)

-              Dem Updater können jetzt über /bname (Base) und /mname (MediaServer) die Dienst-Namen mitgegeben werden, wenn diese nicht unseren Default-Dienstnamen entsprechen. Damit kann der Updater entsprechende Dienste beenden und auch wieder starten.