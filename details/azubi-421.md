# AZUBI-421: IM | Deaktivierte Onlinefunktion wird von infoskop-Base und infoskop-App nicht korrekt berücksichtigt – E-Mails werden weiterhin versendet

## Kategorie
**Bug Fix** | infoskop-Monitor | infoskop-Base | infoskop-App

## Status
✅ **Done** | Resolved: 09.09.2025 | Released in Base 5.0.0

---

## Beschreibung

Wurde die Onlinefunktion (z. B. für E-Mail-Versand) einmal aktiviert und konfiguriert (inkl. Postfach-Zugangsdaten), blieb diese auch nach Deaktivierung über den infoskop-Monitor weiterhin aktiv. E-Mails wurden weiterhin über infoskop-Base versendet – trotz abgeschalteter Onlinefunktion.

### Beobachtetes Verhalten

- Die Onlinefunktion wurde im infoskop-Monitor deaktiviert
- Trotzdem konnten weiterhin E-Mails z. B. über den Bereich "Korrespondenz" in der Patientenkartei versendet werden
- Auch im Hintergrund erfolgte weiterhin ein Versand über die Base
- Die infoskop-App schien die Deaktivierung ebenfalls zu ignorieren

### Reproduktionsschritte

1. Onlinefunktion aktivieren, Postfach-Zugangsdaten einrichten
2. E-Mail-Versand z. B. über Patientenkartei erfolgreich testen
3. Onlinefunktion im infoskop-Monitor deaktivieren
4. Versuchen, über Korrespondenzbereich oder App E-Mails zu versenden
   - **➔ E-Mails wurden dennoch versendet** ❌

### Mögliche Ursache

Die Deaktivierung wurde im System nicht systemweit propagiert oder validiert. Eventuell wurde nur die UI deaktiviert, nicht jedoch die E-Mail-Funktionalität im Hintergrunddienst.

### Zusätzliche Beobachtung

Bei **Neuinstallation ohne Zugangsdaten** war die Mailfunktion zwar verfügbar, aber nicht funktionsfähig.

---

## Lösung

Es wurden die Anzeigen bei deaktivierter Onlinefunktion angepasst. Die Deaktivierung wird nun korrekt systemweit berücksichtigt:
- In infoskop-Base
- In infoskop-Monitor
- In der infoskop-App

E-Mail-Versand ist nach Deaktivierung der Onlinefunktion nicht mehr möglich.

---

## Zugehörige Tickets

### Blocks
- **QS-199**: Quality Assurance Ticket
- **IT-277**: [Test-Case für Online-Funktionen](./it-277.md)

### Relates to
- **[AZUBI-403](./azubi-403.md)**: Zugriff auf Onlineformular-Einstellungen möglich, obwohl Onlineformulare deaktiviert sind
- **INFO-1222**: Weiterführende Implementierung (siehe Kommentare)

---

## Testing

Siehe [IT-277 Test Case](./it-277.md) für detaillierte Testschritte zur Validierung der Deaktivierung.

---

## Technische Details

- **Assignee**: Natascha Schaub
- **Reporter**: Gunther Hohmann
- **Priority**: Missing
- **Labels**: infoskop-Monitor
- **Created**: 21.07.2025
- **Resolved**: 09.09.2025
- **Sprint**: August 2025, Februar/März 2025

---

## Diskussion & Entscheidungen

**Offene Fragen (aus Daily besprochen):**
- **::ORA**: Soll es auch gesperrt werden automatisch wenn die OnlineFunktion nicht aktiviert ist?
- **Automatisierungen**: Sollte die komplette Oberfläche deaktiviert werden?
- **App**: Wie soll der E-Mail-Versand in der App gehandhabt werden?

**Entscheidung:** Bleibt wie es gerade ist (nach Fix). Funktionalität wurde gegengetestet.

---

## Attachments

- `Bildschirmfoto 2025-07-18 um 10.38.39.png` (418 KB)
- `Bildschirmfoto 2025-07-18 um 09.14.23.png` (584 KB)
- `Bildschirmfoto 2025-07-18 um 10.37.27.png` (431 KB)
- `Bildschirmfoto 2025-07-18 um 10.37.50.png` (517 KB)
- `Bildschirmfoto 2025-07-18 um 10.37.38.png` (420 KB)
- `Bildschirmfoto 2025-07-18 um 10.23.46.png` (529 KB)
- `Bildschirmfoto 2025-07-18 um 10.40.23.png` (91 KB)
- `Bildschirmfoto 2025-07-18 um 10.38.18.png` (392 KB)
- `2025-07-18 10.29.55.mp4` (18.8 MB - Demonstration des Problems)
- `Bildschirmfoto 2025-07-18 um 10.23.11.png` (376 KB)

---

## Benutzernutzen

- **Sicherheit**: Keine unbeabsichtigten E-Mail-Versendungen bei deaktivierter Onlinefunktion
- **Konsistenz**: Einheitliches Verhalten über alle Komponenten (Base, Monitor, App)
- **Transparenz**: Klare Funktionalitätsgrenzen je nach Konfiguration
- **Datenschutz**: Verhindert ungewollte Kommunikation nach außen
