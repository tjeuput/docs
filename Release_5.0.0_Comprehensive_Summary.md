# Infoskop-Base Version 5.0.0 - Comprehensive Feature Summary

This document provides a detailed before/after comparison for each component and feature in Release 5.0.0, including test references.

**Note:** "Before" states are only documented when explicitly stated in release notes or bug reports. When unknown, placeholders are used.

---

## 1. infoskop-Base.exe

### Feature: SMTP Email Validation Fix

**Before:**
- E-Mails were displayed as successfully sent even when faulty SMTP server data was configured
- ("E-Mails trotz leere fehlerhafter SMTP-Serverdaten als erfolgreich versendet angezeigt wurden")

**After:**
- [MISSING: How exactly the fix works is not documented - only that the problem was fixed]

**References:**
- Issue: INFO-1243, QS-227

---

## 2. infoskop-Monitor

### Feature 2.1: Embedded Image Resizing in WYSIWYG Editor

**Before:**
- [MISSING: No documentation of previous state - feature described as "Neue Funktion" (new function) and "Option hinzugefügt" (option added)]

**After:**
- Users can now adjust the size of embedded images in email and template texts
- ("Anwender können nun die Größe eingebetteter Bilder in E-Mail- und Vorlagentexten flexibel anpassen")
- Test IT-264 shows functionality includes:
  - Drag & drop image insertion
  - Size adjustment via: 50px, 75px, original size, custom size (popup menu or dragging corners)
  - Adding, editing, and removing links on images
  - Moving images via drag & drop while preserving links
  - Testing across different email clients (iOS, Android, PC, Mac, Webmail, various providers)

**References:**
- Test: IT-264
- Functional Areas Tested:
  - Administration → Settings → Online Forms → System Templates
  - Administration → Settings → Online Forms → Encryption
  - Patient List → Email to Patient
  - Inbox → Reply function
  - Outbox → Resend message
  - Documents → Mail icon
  - Evaluations → PA-Cockpit
  - Evaluations → Bleaching-Cockpit

---

### Feature 2.2: Patient Data Deletion Process

**Before:**
- [MISSING: Release note only states "Der Ablauf der Löschung von Patientendaten im Monitor wurde angepasst und optimiert" - what exactly was changed from before is not documented]

**After:**
- Deletion process was adjusted and optimized (AZUBI-401)
- Test IT-281 shows current functionality:
  - X-icon (3rd from right) in patient list to trigger deletion
  - Dialog "Daten löschen von [Name]" with options:
    - Checkbox "Gesamter Patientendatensatz" (enables/disables sub-options)
    - Checkboxes: "Dokumente", "Anamnesedaten", "Onlinedaten"
    - Date field "Nur Daten bis einschließlich" with date picker and "HEUTE" button
  - Safety features:
    - "Anwenden" button only active when at least one checkbox selected
    - Future dates rejected
    - Only valid dates accepted
    - When "Gesamter Patientendatensatz" selected, date field disabled and ignored
    - Double confirmation dialog: "Bitte bestätigen Sie das Löschen der Daten von [Name]"
    - Warning: "Diese Handlung ist destruktiv. Gelöschte Daten können *nicht* wiederhergestellt werden"
  - When no date selected, all data up to today deleted
- Feature can be enabled/disabled via config: `server/enabledeletion=1`
- Test IT-319 verifies: When disabled (=0), deletion icon (X) is hidden in patient list

**References:**
- Issue: AZUBI-401
- Tests: IT-281, IT-319

---

### Feature 2.3: Link Opening in Mail/Template Texts

**Before:**
- Links in email and template texts could not be opened in local browser
- Links in form link builder (Formularlinkbaukasten) could not be opened in local browser
- ("durch den es nicht möglich war Links in Mail- oder Vorlagentexten, sowie im Formularlinkbaukasten im lokalen Browser zu öffnen")
- [MISSING: What was the problematic behavior in form link builder specifically?]

**After:**
- Links can now be opened in local browser
- Form link builder behavior adjusted: links must now be clicked directly for preview
- ("Verhalten im Formularlinkbaukasten angepasst, sodass Links nun direkt angeklickt werden müssen für eine Vorschau")
- Test IT-262 verifies: In outbox, when clicking linked QR-Code, either nothing happens OR link opens in external browser (must NOT open form within IM)

**References:**
- Test: IT-262
- Issue: QS-177
- Related issues mentioned in release notes

---

### Feature 2.4: Cockpit Icons Update

**Before:**
- Missing icons in cockpits ("fehlende Icons in den Cockpits")

**After:**
- Icons added and updated ("Icons wurden ergänzt und aktualisiert")
- Test IT-256 verifies: Icons visible in PA-Cockpit and Bleaching-Cockpit title areas, preferably matching those in IM menu

**References:**
- Test: IT-256
- Issue: QS-222

---

### Feature 2.5: Bulk Edit in Warning Settings

**Before:**
- [MISSING: Specific issues not documented]

**After:**
- Display behavior of bulk edit in warning settings improved
- ("Das Anzeigeverhalten der Gesamtbearbeitung in den Warnungseinstellungen wurde verbessert")
- Specifically when switching between "Warnungen", "Anamnese", and "Alle"
- And when using "Alles Ja/Nein" option
- ("insbesondere beim Umschalten zwischen „Warnungen", „Anamnese" und „Alle" sowie bei der Nutzung der „Alles Ja/Nein"-Option")

**References:**
- Issue: AZUBI-399

---

### Feature 2.6: Online Function Deactivation Handling

**Before:**
- AZUBI-403: Access to online form settings was still possible despite online forms being deactivated
  - Not accessible via left citizen menu
  - BUT still accessible via general settings page
  - ("Die Onlineformular-Einstellungen sind weiterhin zugänglich")
- AZUBI-421: Deactivated online function was not properly respected by infoskop-Base and infoskop-App
  - Emails could still be sent from correspondence area in patient file
  - Emails continued to be sent by Base in background
  - infoskop-App also ignored the deactivation
  - ("Trotzdem können weiterhin E-Mails z. B. über den Bereich „Korrespondenz" in der Patientenkartei versendet werden")

**After:**
- Displays when online function is deactivated were optimized (AZUBI-403, AZUBI-421, QS-187)
- Test IT-277 verifies when online function deactivated:
  - Settings pages show only "Online-Funktionen aktivieren" toggle
  - Sub-sections (Formulare, Vorlagen, Systemvorlagen, Verschlüsselung) are visible but grayed out and not clickable
  - Access not possible via infoskop-Base settings either
  - Menu entries (Formulare, Vorlagen, Systemvorlagen, Verschlüsselung) locked in Administration → Einstellungen → Onlineformulare
  - Email icons disabled throughout system:
    - Patient menu mail icon locked
    - Inbox menu entry deactivated
    - Outbox menu entry deactivated
    - Documents mail icon locked
    - PA-Cockpit mail icon locked
    - Bleaching-Cockpit mail icon locked (no possibility to send emails)
    - Stage1: no possibility to send emails
- When re-activated and saved (Base restart recommended):
  - All previous settings preserved
  - All online functions accessible and functional again

**References:**
- Issues: AZUBI-403, AZUBI-421, QS-187
- Test: IT-277
- Bug descriptions: AZUBI-403.xml and AZUBI-421.xml

---

### Feature 2.7: ::ORA License Query and Reply Function

**Before:**
- License query for infoskop::ORA had an error (INFO-1194)
- [MISSING: What exactly was the error?]

**After:**
- License query fixed (INFO-1194)
- Reply function is only active for ::ORA customers
- For other users, display was adjusted and function deactivated
- ("Die Antwortfunktion ist nur für ::ORA-Kunden aktiv. Für andere Nutzer wurde die Anzeige angepasst und die Funktion deaktiviert")
- Test IT-279 verifies: When ::ORA not configured, reply icons are disabled in inbox

**References:**
- Issue: INFO-1194
- Test: IT-279

---

### Feature 2.8: Price Handling with Euro Symbol

**Before:**
- Price transfer in PA and Bleaching Cockpit did not work correctly when price contained Euro symbol (€)
- ("Die Preisübernahme im PA- und Bleaching-Cockpit funktioniert nun auch korrekt, wenn der Preis ein Euro-Zeichen (€) enthält")

**After:**
- Price transfer now works correctly even when price contains € symbol

**References:**
- Issue: QS-97

---

### Feature 2.9: Email Template Dropdown

**Before:**
- [MISSING: No documentation of previous state - no test file or release note describes what existed before]

**After:**
- Test IT-317 shows current functionality:
  - Email icon now has dropdown arrow next to envelope icon
  - Clicking arrow opens dropdown with templates
  - Arrow changes direction (down → up when opened)
  - Clicking outside or on arrow again closes dropdown
  - Clicking envelope icon directly opens email window without template
- Available in:
  - Patient menu → Email to patient
  - Documents → Mail icon
  - Evaluations → PA-Cockpit
  - Evaluations → Bleaching-Cockpit

**References:**
- Test: IT-317
- [MISSING: No issue number or release note entry found for this feature]

---

## 3. infoskop::LEA (New Product)

### Feature: Complete New Product Launch

**Before:**
- infoskop::LEA did not exist (new product: "Neues Produkt")

**After:**
- New product "Leistungserfassung (::LEA)" available
- Licensing occurs automatically when setup is correctly completed
- ("Die Lizenzierung erfolgt automatisch, sobald die Einrichtung richtig abgeschlossen ist")
- Release notes document:
  - New webframe integration for client
  - Functions in Base for request management and data storage
  - Automatic license activation when service catalog correctly configured
- Test IT-291 verifies:
  - When ::LEA not installed: no entry visible in infoskop-Client
  - When ::LEA activated and Base + Client restarted: new entry "Leistungserfassung (::LEA)" appears
  - Opens in own window (similar to infoskop-Monitor), separate from Monitor
  - Cannot open ::LEA or IM multiple times
- Test IT-302 verifies login functionality:
  - Login dialog appears on launch
  - "Schließen" closes ::LEA
  - Login without input shows "wird benötigt" under username field
  - Correct login (username: anwender, password: user) succeeds
  - Wrong credentials show red banner "falsche Logindaten"
  - Cannot start multiple ::LEA windows
  - infoskop-Monitor can run simultaneously, both operable
  - Closing one application leaves the other open
  - No automatic re-login (must authenticate each session)
- Test IT-308 verifies window size persistence:
  - Resized window size persists through login/logout
  - Window size persists after closing and reopening ::LEA
- Test IT-313 verifies practitioner display:
  - Treatment overview shows practitioner in "Allgemein"
  - Last selected practitioner remembered for new patients
  - Practitioner name displays correctly in tabular overview (NOT as {#})
- Test IT-310 verifies:
  - New treatment session with no services recorded shows no message in "Allgemein" area

**References:**
- Tests: IT-291, IT-302, IT-308, IT-313, IT-310, IT-319
- Release notes entry for ::LEA

---

## 4. Signexport.exe

### Feature: Proxy Configuration

**Before:**
- [MISSING: Previous state not documented]

**After:**
- Option added to configure proxy
- ("Optimierung: Option hinzugefügt, um einen Proxy zu konfigurieren")

**References:**
- Release notes (no specific test file found)

---

## 5. MediaServerStarter

### Feature 5.1: Service Installation Optimization

**Before:**
- Error existed where installed service names were corrupt and not readable by Windows
- ("behebt einen Fehler, bei dem installierte Dienstnamen korrupt und nicht für Windows leserlich waren")

**After:**
- Installation as service optimized
- Error fixed

**References:**
- Issue: INFO-1157

---

### Feature 5.2: Service Name Documentation

**Before:**
- [MISSING: What was the situation before?]

**After:**
- MediaServerStarter now writes service name to Base-Config to clearly assign multiple installations
- ("der MediaServerStarter speichert Dienstnamen in der Base-Config, um Mehrfachinstallationen klar zuzuordnen")
- Config entry: `Server/mname` = Name of MediaServer service

**References:**
- Release notes

---

## 6. VDDS-stage1.exe

### Feature: Evident Configuration Auto-Recognition

**Before:**
- With Evident Version 6 (after major update March 2025) and infoskop-Base 4.3.1:
  - Extended interface between Evident and infoskop did not work reliably automatically
  - Manual configuration required by technical support/L2
- Automatic Evident configuration was not recognized correctly
- ("welcher die automatische Evident Konfiguration nicht richtig erkannt hat")

**After:**
- Error fixed
- With Evident Version 6 and infoskop-Base 5.0.0:
  - Extended interface between Evident and infoskop automatically configured
  - No manual post-configuration necessary

**References:**
- Issue: INFO-1190, QS-218
- Test: IT-293

---

## 7. Starter.exe

### Feature 7.1: Automatic Restart Monitoring

**Before:**
- [MISSING: What happened when Base became unresponsive?]

**After:**
- Starter.exe now automatically monitors its functionality and restarts independently when problems occur to avoid interruptions
- ("Der Starter.exe überwacht nun automatisch ihre Funktionsfähigkeit und startet sich bei Problemen selbstständig neu, um Unterbrechungen zu vermeiden")
- Configuration flags in Base config.dat (with defaults):
  - `server/restartWhenUnresponsive=1` - When set to 0, Base no longer auto-restarts when Base socket server fails
  - `server/lifesignToBaseInterval=5000` - Interval in which Starter checks Base socket server (in ms)
  - `server/lifesignRestartBusyBaseAfterInterval=30000` - Time Base socket server may be unreachable before restart. Value automatically increases each time Base is terminated to give customers with lengthy tasks a chance to succeed. Resets on restart (in ms)
- Test IT-287 demonstrates:
  - When App sends large PDF (from IT-287 test data), Base becomes unreachable
  - After waiting 30 seconds, Base ≥5.0.0 automatically recovers and restarts via Starter
  - (Base <5.0.0 remains hung and requires manual restart)

**References:**
- Issue: INFO-1187
- Test: IT-287

---

### Feature 7.2: Service Name Documentation

**Before:**
- [MISSING: Previous situation not documented]

**After:**
- Starter writes service names to Base-Config to clearly identify multiple installations
- ("Der Starter speichert Dienstnamen in der Base-Config, um Mehrfachinstallationen eindeutig zuordnen zu können")
- Config entries:
  - `Server/bname` = Name of infoskop-Base service
  - `Server/mname` = Name of MediaServer service

**References:**
- Release notes

---

### Feature 7.3: Error Logging to report.dat

**Before:**
- [MISSING: Was there any logging before?]

**After:**
- In error cases, Starter logs attempts to reach Base in `report.dat`
- This information is also transferred to Logcheck for easier analysis
- ("Der Starter protokolliert im Fehlerfall seine Versuche in report.dat, die Base zu erreichen. Diese Informationen werden auch in den Logcheck übernommen, um die Analyse zu erleichtern")
- Test IT-287 verifies: `report.dat` file exists in Base program folder
- Note: report.dat is part of Logcheck, which may only be current/checkable the next day

**References:**
- Issue: INFO-1187
- Test: IT-287

---

### Feature 7.4: Service Installation Optimization

**Before:**
- Error existed where installed service names were corrupt and not readable by Windows
- ("behebt einen Fehler, bei dem installierte Dienstnamen korrupt und nicht für Windows leserlich waren")

**After:**
- Installation as service optimized
- Error fixed

**References:**
- Issue: INFO-1156

---

### Feature 7.5: HL7 Server Automatic Monitoring

**Before:**
- [MISSING: How was HL7 Server managed before? Was AppToStart the only way?]

**After:**
- HL7 servers now automatically monitored
- When Base-Starter terminates, HL7-Server closes its service "softly", avoiding network problems and long timeouts
- ("HL7-Server werden nun automatisch überwacht. Beim Beenden des Base-Starters schließt der HL7-Server seinen Dienst „sanft", wodurch Netzwerkprobleme und lange Timeouts vermieden werden")
- Configuration flags in Base config.dat (with defaults):
  - `hl7/smartHandling=0` - When set to 1, HL7-Server automatically monitored and softly terminated (requires `hl7/enabled=1`; remove entries from AppToStart beforehand)
  - `hl7/waitforclose=6000` - Time Starter waits for soft termination of HL7-Server before hard kill. Disable with 0 (in ms)
- Test IT-296 explains new socket technology:
  - Old sockets had problems with false/unwanted characters transmitted, disrupting communication
  - New Chilkat Sockets automatically detect if connection still active
  - When connection breaks, old socket closed and new connection automatically established
  - Works for both persistent connections and reconnecting programs
- Test IT-301 verifies with smart handling:
  - HL7 Server process visible in Task Manager
  - HL7 log shows "Using Chilkat Sockets"
  - German umlauts (ä, ö, ü, ß) display correctly in HL7 logs
- Test IT-300 verifies migration for existing customers with running HL7Server

**References:**
- Tests: IT-296 (socket technology), IT-301 (smart handling), IT-300 (existing customer)
- IT-296.xml description

---

## 8. HL7-Server

### Feature: Soft Socket Server Closing

**Before:**
- [MISSING: How did shutdown work before?]

**After:**
- Enables soft closing of socket server
- ("Ermöglicht nun sanftes Schließen des Socket-Servers")
- Configuration flags in HL7-Server config.dat (with defaults):
  - `server/useChilkatSockets=0` - Switch from old sockets to newer socket type with more capabilities - prerequisite for soft closing. Automatically activated when `module/orbis=1` and `server/openstream=1`
- New Chilkat Sockets provide:
  - Automatic connection detection
  - Automatic reconnection when connection drops
  - Elimination of false character transmission issues from old sockets
  - Support for both persistent and reconnecting connection patterns

**References:**
- Tests: IT-296, IT-301
- Works together with Starter.exe HL7 monitoring feature

---

## 9. Infoskop-Client.exe

### Feature 9.1: ::LEA Support

**Before:**
- ::LEA did not exist (new product)

**After:**
- Support for infoskop::LEA
- Calling Windows application as independent window instance
- License query at infoskop-Base.exe
- (See ::LEA section for detailed functionality)

**References:**
- Tests: IT-291, IT-302

---

### Feature 9.2: "Please Wait" Display for Webframes

**Before:**
- [MISSING: What did users see during delayed loading?]

**After:**
- For delayed display of webframes (infoskop-Monitor and infoskop::LEA), users now receive "Bitte warten ..." display making process transparent
- ("Bei längeren Ladezeiten der Webframes in infoskop-Monitor und ::LEA erhalten Nutzer nun eine „Bitte warten …"-Anzeige, die den Prozess transparent macht")

**References:**
- Issue: INFO-1196

---

### Feature 9.3: Multiple Splash Screen Fix

**Before:**
- In Z1, multiple identical splash screens could be loaded simultaneously
- ("bei dem in Z1 mehrere gleichartige Splash-Anzeigen gleichzeitig geladen werden konnten")

**After:**
- Now only one display per execution shown
- ("Nun wird pro Ausführung nur noch eine Anzeige angezeigt")
- Test IT-257 verifies during update process:
  - During installation, splash window appears bottom right on desktop: "Es wurden Updates für infoskop-Base gestartet"
  - After completion, splash window briefly appears: "Updates abgeschlossen" (after infoskop-Client started)

**References:**
- Issue: INFO-1192, QS-193
- Test: IT-257

---

## 10. Infoskop-Base-Updater und infoskop-Base-Setup

### Feature 10.1: Bonjour Installation Changes

**Before:**
- 32-bit Bonjour installation file was included
- [MISSING: What problems existed?]

**After:**
- 32-bit Bonjour installation file removed
- Product now only supports 64-bit and ARM systems
- ("Die Installationsdatei für Bonjour 32Bit wurde entfernt. Das Produkt unterstützt ab sofort nur noch 64‑Bit- und ARM-Systeme")
- Second 64-bit Bonjour installation file added supporting both architectures (Intel and ARM)
- Both installers can be safely installed in parallel in any order
- ("Beide Installer können parallel und in beliebiger Reihenfolge installiert werden")
- Test IT-294 verifies:
  - Fresh installation: Exactly two MSI files in `.../infoskop-Base/Programm/`: `Bonjour64.msi` and `Bonjour64Bit-V3.1.0.1.msi`
  - Update from ≤4.3.1: Three MSI files (two above plus legacy `Bonjour32Bit-V3.1.0.1.msi`)

**References:**
- Issue: INFO-1188
- Test: IT-294

---

### Feature 10.2: Multiple Base Instance Support

**Before:**
- [MISSING: What happened with service names before?]

**After:**
- For installations with multiple Bases on one machine, default service name "infoskop-Base" is no longer automatically assigned to avoid conflicts
- ("Bei Installationen mit mehreren Bases auf einem Rechner wird der Standard-Dienstname „infoskop-Base" nun nicht mehr automatisch vergeben, um Konflikte zu vermeiden")
- Default name "infoskop-Base" only assumed when Updater is NOT given `/MULTIPLEBASES` flag
- Updater can now be given service names via `/bname` (Base) and `/mname` (MediaServer) to correctly stop and restart services when they don't match default service names

**References:**
- Release notes

---

## Summary Statistics

**Total Features Documented:** 28+ features across 10 components

**Test Coverage:**
- IT-256, IT-257, IT-262, IT-264, IT-277, IT-279, IT-281, IT-287, IT-291, IT-293, IT-294, IT-296, IT-300, IT-301, IT-302, IT-308, IT-310, IT-313, IT-317, IT-319
- AZUBI-403, AZUBI-421

**Quality Assurance References:**
- QS-97, QS-177, QS-187, QS-193, QS-218, QS-222, QS-227

**Bug Fixes:**
- INFO-1156, INFO-1157, INFO-1187, INFO-1188, INFO-1190, INFO-1192, INFO-1194, INFO-1196, INFO-1243

**Documentation Gaps:**
Multiple "Before" states are not documented in available materials. This document uses [MISSING: ...] placeholders to indicate where information about previous behavior is not available.
