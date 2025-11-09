# Infoskop-Base Version 5.0.0 - Support Guide

This document provides support-specific information for each feature in Release 5.0.0.

---

## 1. infoskop-Base.exe

### Feature: SMTP Email Validation Fix (INFO-1243, QS-227)

**What Support Needs to Know:**
- **Customer Impact:** Customers will now see accurate error messages when SMTP configuration is wrong
- **How to Verify:** Test email sending with intentionally wrong SMTP settings - should fail with clear error
- **Troubleshooting:** If emails still show as "sent" with wrong SMTP data, verify Base version is 5.0.0+
- **Customer Explanation:** "Previously, the system showed emails as sent even when the mail server wasn't configured correctly. Now you'll get proper error messages if something is wrong with your email settings."
- **[MISSING: What are the specific error messages shown now?]**
- **[MISSING: What log entries should support check?]**

---

## 2. infoskop-Monitor

### Feature 2.1: Embedded Image Resizing in WYSIWYG Editor (IT-264)

**What Support Needs to Know:**
- **How to Enable:** Feature available automatically in all email/template editors
- **Where It Works:**
  - System Templates (Administration → Settings → Online Forms)
  - Encryption templates
  - Patient emails
  - Inbox reply function
  - Outbox resend
  - Documents mail
  - PA-Cockpit
  - Bleaching-Cockpit
- **How to Verify:** Drag & drop image into email editor, try resizing it
- **Known Image Size Options:** 50px, 75px, original, custom (via popup or dragging corners)
- **Troubleshooting:**
  - If images don't resize: Check browser compatibility
  - If images look wrong in received emails: Test across different email clients (iOS, Android, PC, Mac)
- **Customer Explanation:** "You can now resize images in your email templates by dragging the corners or selecting a preset size. This works across all email sending features."
- **[MISSING: File size limits for images?]**
- **[MISSING: Supported image formats?]**
- **[MISSING: What to do if images don't display in certain email clients?]**

---

### Feature 2.2: Patient Data Deletion Process (AZUBI-401, IT-281, IT-319)

**What Support Needs to Know:**
- **How to Enable/Disable:**
  - Edit `config.dat` in Base program folder
  - Add/modify under `[server]` section: `enabledeletion=1` (enable) or `enabledeletion=0` (disable)
  - Restart infoskop-Client for changes to take effect
- **How to Verify:**
  - When enabled (=1): X icon appears in patient list (3rd icon from right)
  - When disabled (=0): X icon hidden
- **User Interface:**
  - Dialog shows: "Daten löschen von [Name]"
  - Options: Complete patient record, Documents, Anamnesis data, Online data
  - Date selector: "Nur Daten bis einschließlich [date]"
  - "HEUTE" button for quick today's date selection
  - Double confirmation required
- **Safety Features:**
  - Future dates rejected automatically
  - Invalid dates prevent deletion
  - Warning: "Diese Handlung ist destruktiv. Gelöschte Daten können *nicht* wiederhergestellt werden"
- **Troubleshooting:**
  - If X icon doesn't appear: Check `server/enabledeletion=1` in config.dat and restart client
  - If deletion fails: Check user permissions
- **Customer Explanation:** "You now have more control over patient data deletion. You can choose exactly what to delete (documents, anamnesis, or online data) and limit deletion to a specific date range. This is a destructive action and cannot be undone."
- **CRITICAL for Support:** This is destructive and irreversible - confirm customer intention before helping enable
- **[MISSING: What exactly was the old deletion process? What changed?]**
- **[MISSING: Are deleted data logged anywhere for audit purposes?]**
- **[MISSING: What happens if deletion fails mid-process?]**

---

### Feature 2.3: Link Opening in Mail/Template Texts (IT-262, QS-177)

**What Support Needs to Know:**
- **What Changed:**
  - Links in emails/templates now open in local browser
  - QR codes in outbox open in external browser (not within IM)
  - Form link builder requires direct click on link for preview
- **How to Verify (IT-262):**
  1. Navigate to Postausgang (Outbox)
  2. Open message with link/QR-Code (don't click "erneut senden")
  3. Click linked QR-Code
  4. Expected: Nothing happens OR opens in external browser (must NOT open within IM)
- **Troubleshooting:**
  - If links don't open: Check default browser settings
  - If QR codes open in IM: Verify Base version is 5.0.0+
- **Customer Explanation:** "Links in emails and templates now open properly in your web browser. QR codes will open in your external browser instead of within the Monitor window."
- **[MISSING: What was the exact problem before - did links not work at all?]**
- **[MISSING: Does this work with all browsers?]**

---

### Feature 2.4: Cockpit Icons Update (IT-256, QS-222)

**What Support Needs to Know:**
- **What Changed:** Icons added to PA-Cockpit and Bleaching-Cockpit title areas
- **Where to Look:**
  - IM → Auswertungen → PA-Cockpit (icon in title area, left of title)
  - IM → Auswertungen → Bleaching-Cockpit (icon in title area, left of title)
- **How to Verify:** Icons should match those in IM menu for consistency
- **Troubleshooting:**
  - If icons missing: Clear browser cache and reload IM
  - Check Monitor version is 5.0.0+
- **Customer Explanation:** "We've added visual icons to the cockpit screens to make them easier to identify and navigate."
- **[MISSING: Do icons have any function or are they purely visual?]**

---

### Feature 2.5: Bulk Edit in Warning Settings (AZUBI-399)

**What Support Needs to Know:**
- **What Improved:** Display behavior when bulk editing warning settings
- **Specific Improvements:**
  - Better switching between "Warnungen", "Anamnese", and "Alle"
  - "Alles Ja/Nein" option works correctly
- **Where to Find:** Administration → Warning Settings → Bulk Edit
- **Troubleshooting:**
  - If bulk edit doesn't work smoothly: Verify Monitor version 5.0.0+
  - Try refreshing the page
- **Customer Explanation:** "Bulk editing in warning settings now works more smoothly when switching between different categories and using the 'All Yes/No' option."
- **[MISSING: What were the specific display issues before?]**
- **[MISSING: How to verify it's working correctly?]**

---

### Feature 2.6: Online Function Deactivation Handling (AZUBI-403, AZUBI-421, QS-187, IT-277)

**What Support Needs to Know:**
- **What Was Broken:**
  - Settings remained accessible even when online functions deactivated
  - Emails could still be sent despite deactivation
  - Inconsistent behavior across Base and App
- **How It Works Now:**
  - When online function deactivated: All related features properly locked/hidden
  - Settings preserved when re-activated
- **How to Test (IT-277):**
  1. IM → Administration → Einstellungen → Onlineformulare
  2. Deactivate "Online-Funktionen aktivieren", save
  3. Verify locked features:
     - Settings show only toggle (Forms, Templates, etc. grayed out)
     - Base settings also locked
     - All menu entries locked (Formulare, Vorlagen, Systemvorlagen, Verschlüsselung)
     - Mail icons disabled in: Patient menu, Inbox, Outbox, Documents, PA-Cockpit, Bleaching-Cockpit, Stage1
  4. Re-activate and save (restart Base recommended)
  5. Verify: All settings preserved, all functions accessible again
- **Troubleshooting:**
  - If email still works when disabled: Restart Base and Client
  - If settings still accessible: Clear browser cache
  - Verify Base version 5.0.0+
- **Customer Explanation:** "When you deactivate online functions, all email and online form features are now properly disabled throughout the system. Your settings are saved and will be restored when you re-activate."
- **Configuration:** No config needed - controlled via UI toggle
- **[MISSING: Does this affect the App immediately or does App need restart?]**
- **[MISSING: What happens to queued emails when deactivated?]**

---

### Feature 2.7: ::ORA License Query and Reply Function (INFO-1194, IT-279)

**What Support Needs to Know:**
- **What Changed:** License query for ::ORA fixed
- **How It Works:** Reply function only active for ::ORA customers
- **How to Verify (IT-279):**
  1. IM → Administration → Modulkonfiguration → ::ORA
  2. Confirm ::ORA not configured (no entry)
  3. Navigate to Posteingang, click reply icon on message
  4. Expected: Reply not possible, function deactivated
  5. Open message, click second reply icon (bottom left)
  6. Expected: Reply not possible, function deactivated
- **Troubleshooting:**
  - If reply function visible without ::ORA: Check Base version 5.0.0+
  - Verify license status in Administration → Modulkonfiguration
- **Customer Explanation:** "The reply function in your inbox is only available if you have an active ::ORA license. This prevents confusion when the feature isn't available."
- **License Check:** Administration → Modulkonfiguration → ::ORA
- **[MISSING: What was the specific error in the license query?]**
- **[MISSING: How to troubleshoot if ::ORA license is valid but reply doesn't work?]**

---

### Feature 2.8: Price Handling with Euro Symbol (QS-97)

**What Support Needs to Know:**
- **What Was Broken:** Price transfer in PA/Bleaching Cockpit failed when price contained €
- **What Works Now:** Price transfer works correctly with or without € symbol
- **Where to Verify:**
  - IM → Auswertungen → PA-Cockpit
  - IM → Auswertungen → Bleaching-Cockpit
- **How to Test:** Enter price with € symbol, verify it transfers correctly
- **Troubleshooting:**
  - If prices still fail with €: Check Monitor version 5.0.0+
  - Try both with and without € to isolate issue
- **Customer Explanation:** "You can now enter prices with the Euro symbol (€) in PA and Bleaching Cockpits, and they'll be processed correctly."
- **[MISSING: What exactly failed - was price saved incorrectly or not at all?]**
- **[MISSING: Does this work with other currency symbols?]**

---

### Feature 2.9: Email Template Dropdown (IT-317)

**What Support Needs to Know:**
- **What's New:** Dropdown arrow next to email icon for quick template selection
- **Where Available:**
  - Patient menu → Email to patient
  - Documents → Mail icon
  - Evaluations → PA-Cockpit
  - Evaluations → Bleaching-Cockpit
- **How to Use:**
  - Click arrow → dropdown opens with templates
  - Click template to select
  - Click envelope icon directly for email without template
  - Arrow changes direction (down ↔ up) when dropdown opens/closes
- **How to Verify (IT-317):** Click dropdown arrow, verify templates appear
- **Troubleshooting:**
  - If dropdown doesn't appear: Check Monitor version 5.0.0+
  - If no templates show: Verify templates exist in system
- **Customer Explanation:** "You can now quickly select email templates from a dropdown next to the email icon, instead of opening the email window first."
- **[MISSING: Was this feature in release notes? No issue number found]**
- **[MISSING: What did users have to do before to select templates?]**

---

## 3. infoskop::LEA (New Product)

### Complete New Product Launch (IT-291, IT-302, IT-308, IT-313, IT-310, IT-319)

**What Support Needs to Know:**
- **What It Is:** New service recording module "Leistungserfassung (::LEA)"
- **License Requirements:** Automatic when service catalog correctly configured
- **How to Check if Active:**
  - Open infoskop-Client
  - Look for menu entry "Leistungserfassung (::LEA)"
  - If not visible: ::LEA not installed/activated
- **How to Launch:**
  - Click "Leistungserfassung (::LEA)" in Client menu
  - Opens in separate window (like Monitor)
  - Cannot open multiple ::LEA windows
  - Can run alongside Monitor
- **Login (IT-302):**
  - Username: anwender
  - Password: user
  - [MISSING: Are these test credentials only? What are real credentials?]
  - No auto-login - must authenticate each session
  - Wrong credentials show red banner: "falsche Logindaten"
  - Empty username shows: "wird benötigt"
- **Window Management (IT-308):**
  - Resized window size persists across sessions
  - Size maintained through login/logout
  - Size persists after closing and reopening
- **Treatment Recording (IT-313):**
  - Last selected practitioner remembered for new patients
  - Practitioner name displays correctly (not as {#})
  - Treatment overview in "Allgemein" section
- **Troubleshooting:**
  - If ::LEA menu entry missing:
    - Verify license/service catalog configuration
    - Restart Base and Client
  - If login fails:
    - Verify credentials
    - Check Base connection
  - If multiple instances open: Should not be possible - report bug
  - If practitioner shows as {#}: Verify Base version 5.0.0+
- **Customer Explanation:** "::LEA is our new service recording module. It runs in its own window alongside the Monitor and lets you track treatments and services for billing purposes."
- **Base Configuration Required:**
  - Service catalog must be correctly configured
  - [MISSING: What exactly must be configured in service catalog?]
- **[MISSING: Full feature list - what can users actually do in ::LEA?]**
- **[MISSING: Where is data stored?]**
- **[MISSING: How to troubleshoot if data doesn't sync?]**
- **[MISSING: Official installation/configuration guide?]**

---

## 4. Signexport.exe

### Feature: Proxy Configuration

**What Support Needs to Know:**
- **What's New:** Option to configure proxy server
- **Where to Configure:** [MISSING: Where exactly is the proxy configuration?]
- **When Needed:** Corporate networks requiring proxy for external connections
- **Configuration Format:** [MISSING: What format? IP:Port? Authentication required?]
- **Troubleshooting:**
  - If Signexport can't connect: Verify proxy settings
  - Check corporate firewall rules
  - Test without proxy first to isolate issue
- **Customer Explanation:** "If you're in a corporate network that requires a proxy server, you can now configure Signexport to use it."
- **[MISSING: How to verify proxy is working?]**
- **[MISSING: What are the proxy configuration parameters?]**
- **[MISSING: Log file location for connection errors?]**

---

## 5. MediaServerStarter

### Feature 5.1: Service Installation Optimization (INFO-1157)

**What Support Needs to Know:**
- **What Was Fixed:** Service names could be corrupt/unreadable by Windows
- **Impact:** More reliable Windows service installation
- **How to Verify:** Check Windows Services - service name should be readable and functional
- **Troubleshooting:**
  - If service won't start: Check Windows Event Viewer
  - Reinstall service with 5.0.0 updater
- **Customer Explanation:** "We fixed an issue where the MediaServer service could have corrupted names in Windows. Services now install and appear correctly."
- **[MISSING: What did corrupt service names look like?]**
- **[MISSING: How to fix existing corrupt services - reinstall only?]**

---

### Feature 5.2: Service Name Documentation

**What Support Needs to Know:**
- **What's New:** Service name written to Base config for reference
- **Where to Find:** `config.dat` in Base program folder
- **Config Entry:** `Server/mname` = MediaServer service name
- **Why Useful:** Track multiple MediaServer instances on same machine
- **How to Use:**
  - Open config.dat
  - Look for `[Server]` section
  - Find `mname=<service name>`
- **Customer Explanation:** "The system now documents custom service names in the configuration file, making it easier to manage multiple installations."
- **[MISSING: When is this written - during installation or runtime?]**
- **[MISSING: Can this be manually edited?]**

---

## 6. VDDS-stage1.exe

### Feature: Evident Configuration Auto-Recognition (INFO-1190, QS-218, IT-293)

**What Support Needs to Know:**
- **What Was Broken:** After Evident V6 update (March 2025), auto-config didn't work with Base 4.3.1
- **What Works Now:** Base 5.0.0 auto-recognizes Evident V6 configuration
- **Test Scenario (IT-293):**
  - Base 4.3.1 + Evident V6: Manual L2 configuration required
  - Base 5.0.0 + Evident V6: Auto-configured, no manual intervention
- **Troubleshooting:**
  - If auto-config fails with Evident V6:
    - Verify Base version 5.0.0+
    - Check Evident version (must be V6 post-March 2025 update)
    - Review VDDS logs
  - If still fails: Fall back to manual configuration (document L2 process)
- **Customer Explanation:** "If you use Evident version 6, the connection now configures automatically. Previously, this required manual technical setup after the Evident update."
- **Evident Version Requirement:** Version 6 (after major update March 2025)
- **[MISSING: What log files show successful auto-recognition?]**
- **[MISSING: What specific settings are auto-configured?]**
- **[MISSING: Manual configuration steps if auto-config fails?]**

---

## 7. Starter.exe

### Feature 7.1: Automatic Restart Monitoring (INFO-1187, IT-287)

**What Support Needs to Know:**
- **What's New:** Starter monitors Base and auto-restarts when unresponsive
- **Configuration (Base config.dat):**
  ```
  [server]
  restartWhenUnresponsive=1    # 1=enabled, 0=disabled
  lifesignToBaseInterval=5000  # Check interval in ms (default 5 seconds)
  lifesignRestartBusyBaseAfterInterval=30000  # Timeout before restart in ms (default 30 seconds)
  ```
- **How It Works:**
  - Starter pings Base socket server every 5 seconds (default)
  - If unreachable for 30 seconds (default): Auto-restart
  - Timeout increases automatically after each restart (allows long operations to eventually succeed)
  - Timeout resets on restart
- **Test Scenario (IT-287):**
  1. App sends large PDF to Base
  2. Base becomes unreachable
  3. Wait 30 seconds
  4. Base 5.0.0: Auto-recovers and restarts
  5. Base <5.0.0: Remains hung, requires manual restart
- **How to Verify:**
  - Check `report.dat` in Base program folder
  - Logs restart attempts
  - Content transferred to Logcheck (may be next-day)
- **Troubleshooting:**
  - If Base keeps restarting: Check `report.dat` for patterns
  - Increase timeout: Modify `lifesignRestartBusyBaseAfterInterval` to higher value
  - Disable if needed: Set `restartWhenUnresponsive=0`
  - If restart doesn't happen: Verify config parameters, check Starter is running
- **Customer Explanation:** "The system now monitors itself and automatically restarts if it becomes unresponsive. This prevents situations where the Base hangs and requires manual intervention."
- **IMPORTANT:** This protects against Base hanging but logs all attempts in report.dat for troubleshooting
- **[MISSING: What happens to in-progress operations during restart?]**
- **[MISSING: How to determine optimal timeout for customer's environment?]**
- **[MISSING: Does this work with Base as Windows service?]**

---

### Feature 7.2: Service Name Documentation

**What Support Needs to Know:**
- **What's New:** Service names written to Base config for reference
- **Where to Find:** `config.dat` in Base program folder
- **Config Entries:**
  ```
  [Server]
  bname=<Base service name>
  mname=<MediaServer service name>
  ```
- **Why Useful:** Identify services in multi-instance setups
- **How to Use:**
  - Open config.dat
  - Look for `[Server]` section
  - Find `bname` and `mname` values
- **Customer Explanation:** "The system now tracks custom service names in the configuration, making it easier to manage multiple installations on the same server."
- **[MISSING: When are these written - installation or runtime?]**

---

### Feature 7.3: Error Logging to report.dat (INFO-1187, IT-287)

**What Support Needs to Know:**
- **What's New:** Starter logs Base connection attempts in report.dat
- **Log Location:** Base program folder (same location as config.dat)
- **What's Logged:** Starter's attempts to reach Base during failures
- **Log Integration:** Content also transferred to Logcheck (next-day update)
- **How to Use:**
  1. Navigate to Base program folder
  2. Open `report.dat`
  3. Review connection attempt history
  4. Check Logcheck for consolidated view (may be next day)
- **Troubleshooting:**
  - If report.dat missing: Verify Base 5.0.0+ and Starter has write permissions
  - If logs not in Logcheck: Wait until next day, Logcheck updates daily
- **Customer Explanation:** "The system now logs all connection issues for later review, making it easier to diagnose intermittent problems."
- **[MISSING: What does a typical report.dat entry look like?]**
- **[MISSING: How long are logs retained?]**
- **[MISSING: File format - plain text or structured?]**

---

### Feature 7.4: Service Installation Optimization (INFO-1156)

**What Support Needs to Know:**
- Same as MediaServerStarter Feature 5.1 - see above
- **[MISSING: Same questions apply]**

---

### Feature 7.5: HL7 Server Automatic Monitoring (IT-296, IT-301, IT-300)

**What Support Needs to Know:**
- **What's New:**
  - Automatic HL7 Server monitoring (independent of AppToStart)
  - "Soft close" prevents network timeout issues
  - New Chilkat Sockets eliminate false character issues
- **Configuration (Base config.dat):**
  ```
  [hl7]
  enabled=1           # Must be enabled for HL7 functionality
  smartHandling=1     # Enable automatic monitoring and soft close
  waitforclose=6000   # Wait time for soft close in ms (0=disabled)
  ```
- **Configuration (HL7-Server config.dat):**
  ```
  [server]
  useChilkatSockets=1  # Enable new socket technology (required for soft close)
  ```
- **Prerequisites:**
  - Remove HL7 entries from AppToStart before enabling smartHandling
  - Requires `hl7/enabled=1`
- **How to Verify (IT-301):**
  1. Check Task Manager: HL7Server.exe process visible
  2. Check HL7 logs (.../infoskop-Base/HL7Server/HL7Log/):
     - Should show "Using Chilkat Sockets"
     - German umlauts (ä, ö, ü, ß) display correctly
  3. Send test HL7 message via SmartHL7 Sender
  4. Verify data appears correctly in log
- **Migration for Existing Customers (IT-300):**
  - Before: HL7Server managed via AppToStart, no smartHandling, no useChilkatSockets
  - After: Add configs, remove from AppToStart, restart Base
  - Verify same functionality works
- **New Socket Technology Benefits (IT-296):**
  - Old sockets: False/unwanted characters disrupted communication
  - Chilkat Sockets: Auto-detect connection status, auto-reconnect on disconnect
  - Supports both persistent and reconnecting connection patterns
- **Troubleshooting:**
  - If HL7Server not visible in Task Manager:
    - Verify `hl7/enabled=1` in Base config.dat
    - Check Base restart completed successfully
  - If "Using Chilkat Sockets" not in log:
    - Verify `server/useChilkatSockets=1` in HL7-Server config.dat
    - Restart Base
  - If umlauts display incorrectly:
    - Verify using Chilkat Sockets
    - Check file encoding
  - If network timeouts still occur:
    - Verify `hl7/smartHandling=1`
    - Check `hl7/waitforclose` value (increase if needed)
- **Customer Explanation:** "We've modernized the HL7 connection handling. The system now uses better socket technology that prevents character corruption and network timeout issues. The HL7 server also shuts down gracefully instead of abruptly."
- **CRITICAL:** Remove AppToStart entries before enabling smartHandling
- **[MISSING: What happens if AppToStart and smartHandling both enabled?]**
- **[MISSING: How to verify soft close is working vs. hard kill?]**
- **[MISSING: Compatibility with specific HL7 versions/systems?]**
- **[MISSING: What are typical waitforclose values for different scenarios?]**

---

## 8. HL7-Server

### Feature: Soft Socket Server Closing (IT-296, IT-301)

**What Support Needs to Know:**
- Same as Starter.exe Feature 7.5 - HL7 Server components
- See above for configuration and troubleshooting
- **[MISSING: Same questions apply]**

---

## 9. Infoskop-Client.exe

### Feature 9.1: ::LEA Support (IT-291, IT-302)

**What Support Needs to Know:**
- See Section 3 "infoskop::LEA (New Product)" for full details
- Client provides menu entry and window launching
- License validation handled by Base

---

### Feature 9.2: "Please Wait" Display for Webframes (INFO-1196)

**What Support Needs to Know:**
- **What's New:** "Bitte warten ..." message during webframe loading
- **Where Appears:** When loading Monitor or ::LEA
- **Purpose:** User feedback during delayed webframe initialization
- **How to Verify:** Start Monitor or ::LEA, look for loading message
- **Troubleshooting:**
  - If message doesn't appear but loading takes long: Check Client version 5.0.0+
  - If loading never completes: Check Base connection, network connectivity
- **Customer Explanation:** "You'll now see a 'Please wait...' message when the Monitor or ::LEA is loading, so you know the system is working."
- **[MISSING: What did users see before - blank screen?]**
- **[MISSING: How long is typical loading time?]**
- **[MISSING: What if loading message appears but never completes?]**

---

### Feature 9.3: Multiple Splash Screen Fix (INFO-1192, QS-193, IT-257)

**What Support Needs to Know:**
- **What Was Broken:** Multiple identical splash screens could appear in Z1
- **What Works Now:** Only one splash screen per execution
- **When Visible (IT-257):**
  - During update: Bottom-right desktop: "Es wurden Updates für infoskop-Base gestartet"
  - After completion: "Updates abgeschlossen" (after Client starts)
- **How to Verify:** Trigger update, watch for single splash screen
- **Troubleshooting:**
  - If multiple splashes appear: Verify Client version 5.0.0+
  - Report as regression
- **Customer Explanation:** "We fixed an issue where multiple update notification windows could appear. You'll now only see one notification at a time."
- **[MISSING: What is Z1 specifically?]**
- **[MISSING: What caused multiple splashes before?]**

---

## 10. Infoskop-Base-Updater und infoskop-Base-Setup

### Feature 10.1: Bonjour Installation Changes (INFO-1188, IT-294)

**What Support Needs to Know:**
- **What Changed:**
  - Removed: Bonjour 32-bit support
  - Added: Second 64-bit installer for ARM compatibility
  - Product now: 64-bit and ARM only
- **Installation Files:**
  - Fresh install: 2 MSI files
    - `Bonjour64.msi`
    - `Bonjour64Bit-V3.1.0.1.msi`
  - Update from ≤4.3.1: 3 MSI files (above + legacy `Bonjour32Bit-V3.1.0.1.msi`)
- **How It Works:**
  - Both 64-bit installers can run in any order, in parallel
  - Only one will actually work (depends on architecture: Intel vs. ARM)
  - Both can be safely attempted
- **How to Verify (IT-294):**
  - Navigate to `.../infoskop-Base/Programm/`
  - Count MSI files matching pattern above
- **Troubleshooting:**
  - If 32-bit system: Not supported in 5.0.0+ (must stay on 4.x)
  - If Bonjour won't install: Try both 64-bit installers
  - Check architecture (Intel vs. ARM)
- **Customer Explanation:** "We've updated Bonjour support to 64-bit and ARM systems only. If you're on 32-bit Windows, please contact support before upgrading."
- **CRITICAL:** 32-bit systems NOT supported - check before upgrade
- **[MISSING: How to determine if customer is on 32-bit before upgrade?]**
- **[MISSING: Migration path for 32-bit customers?]**
- **[MISSING: What functionality breaks without Bonjour?]**

---

### Feature 10.2: Multiple Base Instance Support

**What Support Needs to Know:**
- **What's New:** Better handling of multiple Base instances on same machine
- **Default Behavior:**
  - Without `/MULTIPLEBASES` flag: Uses "infoskop-Base" as service name
  - With `/MULTIPLEBASES` flag: Requires custom service names
- **Updater Parameters:**
  - `/bname <name>` - Custom Base service name
  - `/mname <name>` - Custom MediaServer service name
- **Why Useful:**
  - Prevents service name conflicts
  - Updater can properly stop/restart custom-named services
- **How to Use:**
  ```
  infoskop-Base-Updater.exe /bname "infoskop-Base-Practice1" /mname "MediaServer-Practice1"
  ```
- **Troubleshooting:**
  - If updater can't stop service: Verify service name matches `/bname` parameter
  - Check Windows Services for actual service name
  - Ensure no conflicting services
- **Customer Explanation:** "If you run multiple infoskop installations on one server, you can now give each one a unique name. The updater will correctly manage each instance."
- **[MISSING: Full list of updater command-line parameters?]**
- **[MISSING: How to rename existing service to avoid conflicts?]**
- **[MISSING: What happens if updater can't find the named service?]**

---

## General Support Resources

### Version Verification
- **Base:** Administration → About or check installation path
- **Monitor:** Login screen or About section
- **Client:** Help → About

### Log Locations
- **Base Logs:** `.../infoskop-Base/Programm/` folder
- **HL7 Logs:** `.../infoskop-Base/HL7Server/HL7Log/`
- **Report.dat:** `.../infoskop-Base/Programm/report.dat`
- **Logcheck:** [MISSING: Where is Logcheck located?]

### Configuration File
- **Location:** `.../infoskop-Base/Programm/config.dat`
- **Format:** INI-style sections and key-value pairs
- **Editing:** Stop Base service before editing, restart after
- **Backup:** Always backup before manual editing

### Common Troubleshooting Steps
1. Verify version 5.0.0+ for all components
2. Restart Base service and Client
3. Clear browser cache (for Monitor/LEA issues)
4. Check config.dat for correct parameters
5. Review logs (report.dat, HL7 logs, Logcheck)
6. Verify Windows service status
7. Check network connectivity
8. Verify license status

### [MISSING CRITICAL INFORMATION]
The following information would significantly help support teams:

**General:**
- Official upgrade guide from 4.x to 5.0.0
- Rollback procedure if upgrade fails
- Known issues and workarounds
- System requirements (Windows versions, hardware)

**Configuration:**
- Complete config.dat reference guide
- Default values for all parameters
- Parameter dependencies
- Safe vs. unsafe parameters to modify

**Logging:**
- Log file formats and interpretation guide
- Log rotation policies
- How to increase log verbosity
- What to look for in different log types

**Licensing:**
- How to verify all license components
- What features require which licenses
- How to troubleshoot license validation issues

**Integration:**
- Compatibility matrix (Evident versions, HL7 systems, etc.)
- Known third-party integration issues
- Certificate/security requirements

**Performance:**
- Expected load times for different features
- Resource requirements (CPU, RAM, disk)
- Network bandwidth requirements
- Database maintenance schedules

**Backup/Recovery:**
- What to backup before upgrade
- How to restore if upgrade fails
- Patient data backup procedures
- Configuration backup procedures
