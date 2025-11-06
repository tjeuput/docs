# AZUBI-403: IM | Zugriff auf Onlineformular-Einstellungen möglich, obwohl Onlineformulare deaktiviert sind

## Kategorie
**Bug Fix** | infoskop-Monitor

## Status
✅ **Done** | Resolved: 08.09.2025 | Released in Base 5.0.0

---

## Beschreibung

Trotz deaktivierter Onlineformulare war der Zugriff auf die zugehörigen Einstellungen weiterhin möglich – sowohl über infoskop-Base als auch über infoskop-Monitor. Dieses Verhalten war unerwünscht.

### Reproduktionsschritte

1. In **infoskop-Base** die **Onlineformulare deaktivieren**
2. In **infoskop-Monitor** zur Seite **"infoskop-Einstellungen"** navigieren
3. ➔ Die **Onlineformular-Einstellungen** waren weiterhin zugänglich:
   - Nicht über das linke **Bürger-Menü**
   - Aber **über die allgemeine Einstellungsseite**
4. Auch nach **Neuinstallation** und erneutem **Deaktivieren der Onlineformulare** blieb dieser Zugriff bestehen

### Problembereiche

Die folgenden Menüpunkte waren fälschlicherweise noch erreichbar:
- **Formulare**
- **Vorlagen**
- **Systemvorlagen**
- **Verschlüsselung**

---

## Lösung

Die Anzeigen bei deaktivierter Onlinefunktion wurden angepasst. Alle Onlineformular-bezogenen Einstellungen werden nun korrekt ausgeblendet oder deaktiviert, wenn die Onlinefunktion nicht aktiv ist.

---

## Zugehörige Tickets

### Blocks
- **IT-277**: [Test-Case für Online-Funktionen](./it-277.md)
- **QS-187**: Quality Assurance Ticket

### Relates to
- **[AZUBI-421](./azubi-421.md)**: Deaktivierte Onlinefunktion wird von infoskop-Base und infoskop-App nicht korrekt berücksichtigt

---

## Testing

Siehe [IT-277 Test Case](./it-277.md) für detaillierte Testschritte.

---

## Technische Details

- **Assignee**: Natascha Schaub
- **Reporter**: Gunther Hohmann
- **Priority**: Missing
- **Created**: 11.07.2025
- **Resolved**: 08.09.2025
- **Sprint**: August 2025, Februar/März 2025

---

## Attachments

- `Bildschirmfoto 2025-07-11 um 10.58.28.png` (669 KB)
- `2025-07-11 09.20.01.mp4` (8.4 MB - Demonstration des Problems)
- `online menu.mp4` (1.6 MB - Nach Fix)

---

## Benutzernutzen

- Verhindert verwirrende Zugriffe auf nicht verfügbare Funktionen
- Klarere Benutzerführung bei deaktivierten Features
- Konsistente Erfahrung zwischen infoskop-Base und infoskop-Monitor
