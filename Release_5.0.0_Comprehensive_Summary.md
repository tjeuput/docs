# Infoskop-Base Version 5.0.0 - Comprehensive Feature Summary

This document provides a detailed before/after comparison for each component and feature in Release 5.0.0, including test references.

---

## 1. infoskop-Base.exe

### Feature: SMTP Email Validation Fix

**Before:**
- Emails were shown as successfully sent even when incorrect SMTP server data was configured
- Users received false positive feedback despite failed email delivery
- No proper validation of SMTP configuration

**After:**
- System properly validates SMTP server configuration before attempting to send emails
- Accurate error messages when SMTP data is incorrect
- Emails are only marked as "sent" when actually delivered successfully

**References:**
- Issue: INFO-1243, QS-227

---

## 2. infoskop-Monitor

### Feature 2.1: Embedded Image Resizing in WYSIWYG Editor

**Before:**
- Embedded images in email and template texts had fixed sizes
- Users could not adjust image dimensions flexibly
- Limited control over email content layout

**After:**
- Users can now flexibly resize embedded images in emails and templates
- Images can be adjusted via:
  - Predefined sizes (50px, 75px, original size)
  - Custom sizes through popup menu
  - Dragging corners to resize
- Supports drag & drop image insertion
- Links remain intact when images are moved
- Images display correctly across different email clients (iOS, Android, PC, Mac, Webmail)

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
- Patient data deletion process was less organized
- Limited control over what specific data to delete
- No granular date-based deletion options

**After:**
- Optimized deletion workflow with improved UI
- Granular deletion options:
  - Complete patient record (enables/disables all sub-options)
  - Documents
  - Anamnesis data
  - Online data
- Date-based deletion: "Only data up to and including [date]"
- Date picker with "TODAY" button for convenience
- Safety features:
  - Future dates are rejected
  - Only valid dates accepted
  - Double confirmation dialog
  - Warning: "This action is destructive. Deleted data cannot be restored"
- Feature can be enabled/disabled via config: `server/enabledeletion=1`
- When disabled, deletion icon (X) is hidden in patient list

**References:**
- Issue: AZUBI-401
- Tests: IT-281, IT-319

---

### Feature 2.3: Link Opening in Mail/Template Texts

**Before:**
- Links in email and template texts could not be opened in local browser
- Links in the form link builder (Formularlinkbaukasten) had problematic behavior
- QR codes in outbox opened forms within Monitor instead of external browser
- Users had to click entire preview area to access links

**After:**
- Links can now be opened correctly in local browser
- Form link builder behavior improved: links must be clicked directly for preview
- QR codes in outbox either do nothing or open in external browser (not within IM)
- Proper link handling across all email and template contexts

**References:**
- Test: IT-262
- Issue: QS-177
- Description in IT-262.xml: Tests QR-Code opening behavior in outbox

---

### Feature 2.4: Cockpit Icons Update

**Before:**
- Missing icons in PA-Cockpit and Bleaching-Cockpit
- Inconsistent icon display in evaluation areas
- Title areas lacked visual elements

**After:**
- Icons added to PA-Cockpit and Bleaching-Cockpit title areas
- Icons match those used in Monitor menu for consistency
- Improved visual appearance and user orientation

**References:**
- Test: IT-256
- Issue: QS-222

---

### Feature 2.5: Bulk Edit in Warning Settings

**Before:**
- Suboptimal display behavior when bulk editing warning settings
- Issues when switching between "Warnings", "Anamnesis", and "All"
- "All Yes/No" option did not work reliably

**After:**
- Improved bulk edit functionality in warning settings
- Smooth switching between different warning categories
- "All Yes/No" option works correctly
- Better visual feedback during bulk operations

**References:**
- Issue: AZUBI-399

---

### Feature 2.6: Online Function Deactivation Handling

**Before:**
- Online forms settings remained accessible even when online function was deactivated
- Email functionality continued to work despite deactivated online function
- Inconsistent UI state when online features were disabled
- Settings accessible via both citizen menu and general settings page

**After:**
- When online function is deactivated:
  - Settings pages show only "Activate Online Functions" toggle
  - Sub-sections (Forms, Templates, System Templates, Encryption) are grayed out and not clickable
  - Menu entries in Administration → Settings → Online Forms are locked
  - Email icons are disabled throughout the system:
    - Patient list mail icon
    - Inbox and Outbox are deactivated
    - Documents mail icon
    - PA-Cockpit mail icon
    - Bleaching-Cockpit mail icon
    - Stage1 email functionality
- When re-activated:
  - All previous settings are preserved
  - All online functions become accessible and functional again
- Proper enforcement across both infoskop-Base and infoskop-Monitor

**References:**
- Issues: AZUBI-403, AZUBI-421, QS-187
- Tests: IT-277
- Detailed Bug Descriptions:
  - AZUBI-403: Access to online form settings possible despite deactivation
  - AZUBI-421: Deactivated online function not respected by Base and App - emails still sent

---

### Feature 2.7: ::ORA License Query

**Before:**
- License query for infoskop::ORA had errors
- Unreliable license validation

**After:**
- Fixed license query mechanism
- ::ORA functionality only available when properly licensed
- Reply function disabled for non-::ORA customers
- Proper display and activation based on license status

**References:**
- Issue: INFO-1194
- Test: IT-279
- Verification: Checks that reply icons are disabled when ::ORA is not configured

---

### Feature 2.8: Price Handling with Euro Symbol

**Before:**
- Price transfer in PA and Bleaching Cockpit failed when price contained € symbol
- Data entry with currency symbols caused errors

**After:**
- Price handling works correctly even when Euro symbol (€) is included
- Proper parsing and processing of prices with currency formatting

**References:**
- Issue: QS-97

---

### Feature 2.9: Email Template Dropdown

**Before:**
- Email icon only opened empty email window
- Users had to manually select templates after opening email dialog
- No quick access to email templates

**After:**
- Email icons now have dropdown arrow next to envelope icon
- Clicking arrow reveals dropdown with available templates
- Arrow changes direction (up/down) based on dropdown state
- Available in multiple locations:
  - Patient menu → Email to patient
  - Documents → Mail icon
  - Evaluations → PA-Cockpit
  - Evaluations → Bleaching-Cockpit
- Direct email (without template) still possible by clicking envelope icon directly

**References:**
- Test: IT-317

---

## 3. infoskop::LEA (New Product)

### Feature: Complete New Product Launch

**Before:**
- infoskop::LEA did not exist
- No dedicated service recording module
- Limited treatment documentation options

**After:**
- New standalone product "Leistungserfassung (::LEA)" integrated
- Available as separate window instance (similar to Monitor)
- Automatic licensing when correctly configured with service catalog
- Client Support:
  - Windows application launches as independent window
  - License validation via infoskop-Base.exe
  - Cannot open multiple instances simultaneously
  - Can run alongside infoskop-Monitor
- Login System:
  - Dedicated login dialog (username/password required)
  - No automatic re-login (must authenticate each session)
  - Error feedback for wrong credentials ("falsche Logindaten")
  - Field validation (username required)
- Window Management:
  - Customizable window size persists across sessions
  - Size maintained through login/logout cycles
- Treatment Recording:
  - Treatment overview with practitioner selection
  - Last selected practitioner remembered and pre-selected for new patients
  - Practitioner name displays correctly in overview (no placeholder like {#})
  - Treatment session tracking
  - Service recording functionality
- Base Functions:
  - Request management in Base
  - Data storage functions

**References:**
- Tests: IT-291 (LEA activation and window launch), IT-302 (Login functionality), IT-308 (Window size persistence), IT-313 (Practitioner name display), IT-310 (New messages), IT-319 (Deletion logic)
- Related test file descriptions show comprehensive LEA functionality testing

---

## 4. Signexport.exe

### Feature: Proxy Configuration

**Before:**
- No proxy configuration option available
- Limited network configuration flexibility
- Issues in environments requiring proxy servers

**After:**
- Added option to configure proxy server
- Better support for restricted network environments
- Improved connectivity in corporate networks

**References:**
- Mentioned in release notes (no specific test file found)

---

## 5. MediaServerStarter

### Feature 5.1: Service Installation Optimization

**Before:**
- Service names could become corrupted during installation
- Service names were not readable by Windows
- Caused service management issues

**After:**
- Fixed service installation process
- Service names are properly formatted and Windows-readable
- Reliable service registration

**References:**
- Issue: INFO-1157

---

### Feature 5.2: Service Name Documentation

**Before:**
- Custom service names were not documented
- Difficult to track multiple MediaServer instances on same machine

**After:**
- MediaServerStarter now writes service name to Base config
- Config entry: `Server/mname` = Name of MediaServer service
- Enables clear identification of multiple installations
- Supports scenarios with multiple MediaServers on one machine

**References:**
- Mentioned in release notes

---

## 6. VDDS-stage1.exe

### Feature: Evident Configuration Auto-Recognition

**Before:**
- After Evident Version 6 major update (March 2025), automatic configuration did not work reliably
- Extended interface between Evident and infoskop required manual configuration by technical support (L2)
- Version 6 configuration not properly recognized

**After:**
- Automatic Evident configuration recognition now works correctly
- Extended interface configures automatically with Evident Version 6
- No manual technical intervention needed
- Seamless integration with Evident after major update

**References:**
- Issue: INFO-1190, QS-218
- Test: IT-293

---

## 7. Starter.exe

### Feature 7.1: Automatic Restart Monitoring

**Before:**
- When Base became unresponsive, it remained hung
- No automatic recovery from TCP socket server failures
- Users had to manually restart Base
- Long-running operations could fail without recovery option

**After:**
- Starter automatically monitors Base TCP socket server functionality
- Automatic restart triggered when Base becomes unresponsive
- Intelligent timeout system:
  - Initial timeout: 30 seconds (default)
  - Timeout automatically increases after each restart
  - Allows users with lengthy operations to eventually succeed through retries
- Configurable via Base config:
  - `server/restartWhenUnresponsive=1` (0 to disable auto-restart)
  - `server/lifesignToBaseInterval=5000` (check interval in ms)
  - `server/lifesignRestartBusyBaseAfterInterval=30000` (timeout before restart in ms)
  - Timeout resets on restart
- Protects against scenarios where Base becomes unreachable (e.g., when App sends large PDFs)
- After 30 seconds, Base automatically recovers and restarts

**References:**
- Issue: INFO-1187
- Test: IT-287
- Test demonstrates: App sending PDF → Base becomes unreachable → Automatic recovery within 30 seconds

---

### Feature 7.2: Service Name Documentation

**Before:**
- Custom service names for Base and MediaServer were not documented
- Difficult to manage multiple Base instances on same machine

**After:**
- Starter writes service names to Base config for future reference
- Config entries:
  - `Server/bname` = Name of infoskop-Base service
  - `Server/mname` = Name of MediaServer service
- Enables proper identification in multi-instance scenarios

**References:**
- Mentioned in release notes

---

### Feature 7.3: Error Logging to report.dat

**Before:**
- Starter's attempts to reach Base in error situations were not documented
- Difficult to diagnose connection issues
- No visibility into restart attempts

**After:**
- Starter logs connection attempts to `report.dat` file
- Log content is transferred to Logcheck
- Better troubleshooting and diagnostic capabilities
- Visible alongside automated restart functionality

**References:**
- Issue: INFO-1187
- Test: IT-287 verifies presence of report.dat file

---

### Feature 7.4: Service Installation Optimization

**Before:**
- Service names could become corrupted
- Service names not readable by Windows
- Installation issues in service mode

**After:**
- Fixed service installation bugs
- Proper service name formatting
- Reliable Windows service registration

**References:**
- Issue: INFO-1156

---

### Feature 7.5: HL7 Server Automatic Monitoring

**Before:**
- HL7 Server had to be managed via AppToStart mechanism
- Hard termination of HL7 Server caused socket timeout issues
- Network errors with long timeouts at some customer sites
- Socket connections not properly closed on shutdown

**After:**
- Automatic HL7 Server monitoring (independent of AppToStart)
- "Soft close" functionality when Base-Starter terminates:
  - HL7 Server closes socket server properly before self-termination
  - Prevents network errors and long timeouts
  - Proper connection cleanup
- New Chilkat Sockets technology for better connection stability
- Automatic detection when connections drop, with auto-reconnect
- Eliminates false character transmission issues from old sockets
- Configuration via Base config.dat:
  - `hl7/smartHandling=1` enables automatic monitoring and soft close (requires `hl7/enabled=1`)
  - `hl7/waitforclose=6000` wait time for soft close before hard kill (in ms, 0 to disable)
- HL7 Server process visible in Task Manager
- Supports both persistent and reconnecting connection patterns

**References:**
- Tests: IT-296 (new socket technology verification), IT-301 (smart handling with new configs), IT-300 (existing customer migration)
- IT-296.xml explains: New Chilkat Sockets eliminate false character issues and provide stable auto-reconnect
- Test IT-301 verifies: German umlauts (ä, ö, ü, ß) display correctly in HL7 logs

---

## 8. HL7-Server

### Feature: Soft Socket Server Closing

**Before:**
- Socket server terminated abruptly
- Network timeout issues
- Connection problems at some customer sites
- Old socket technology with reliability issues

**After:**
- Enables soft closing of socket server
- Graceful shutdown process
- Reduced network errors
- Configuration via HL7-Server config.dat:
  - `server/useChilkatSockets=1` enables new socket technology (prerequisite for soft close)
  - Automatically activated when `module/orbis=1` and `server/openstream=1`
- New Chilkat Sockets provide:
  - Stable connection detection
  - Automatic reconnection when connection drops
  - Better handling of persistent and reconnecting clients

**References:**
- Tests: IT-296, IT-301
- Requirement: Works with Starter.exe HL7 monitoring feature

---

## 9. Infoskop-Client.exe

### Feature 9.1: ::LEA Support

**Before:**
- No client-side support for ::LEA
- Could not launch ::LEA from client interface

**After:**
- Menu entry "Leistungserfassung (::LEA)" appears when activated
- Launches ::LEA as independent Windows application instance
- License validation with infoskop-Base.exe
- Single instance enforcement (cannot open multiple ::LEA windows)
- Works alongside infoskop-Monitor

**References:**
- Tests: IT-291, IT-302
- Part of overall ::LEA integration

---

### Feature 9.2: "Please Wait" Display for Webframes

**Before:**
- During delayed loading of webframes (Monitor, ::LEA), users saw blank screen
- No feedback during loading process
- Unclear whether application was starting or hung

**After:**
- "Bitte warten ..." (Please wait ...) message displays during webframe loading
- Transparent process feedback
- Better user experience during startup
- Applies to both infoskop-Monitor and ::LEA

**References:**
- Issue: INFO-1196

---

### Feature 9.3: Multiple Splash Screen Fix

**Before:**
- In Z1, multiple identical splash screens could appear simultaneously
- Confusing user experience
- Resource waste from duplicate displays

**After:**
- Only one splash screen per execution allowed
- Cleaner startup experience
- Proper splash screen management

**References:**
- Issue: INFO-1192, QS-193
- Test: IT-257 (verifies single splash behavior during update process)

---

## 10. Infoskop-Base-Updater und infoskop-Base-Setup

### Feature 10.1: Bonjour Installation Changes

**Before:**
- Included Bonjour 32-bit installation file
- Single Bonjour installer that didn't work on all architectures
- Compatibility issues with ARM systems

**After:**
- Removed Bonjour 32-bit installation file
- Product now supports only 64-bit and ARM systems
- Two 64-bit Bonjour installers included:
  - `Bonjour64.msi`
  - `Bonjour64Bit-V3.1.0.1.msi`
- Each installer supports different architectures (Intel and ARM)
- Both can be safely installed in parallel in any order
- In practice, only one installer works per architecture
- Fresh installations contain only two MSI files
- Updates from version ≤4.3.1 retain old `Bonjour32Bit-V3.1.0.1.msi` (legacy file)

**References:**
- Issue: INFO-1188
- Test: IT-294

---

### Feature 10.2: Multiple Base Instance Support

**Before:**
- Default service name "infoskop-Base" automatically assigned
- Conflicts when multiple Bases installed on same machine

**After:**
- Default name "infoskop-Base" only used when `/MULTIPLEBASES` flag is NOT set
- Prevents service name conflicts in multi-instance scenarios
- Updater accepts custom service names:
  - `/bname` (Base service name)
  - `/mname` (MediaServer service name)
- Updater can properly stop and restart services with custom names

**References:**
- Mentioned in release notes
- Supports enterprise scenarios with multiple Base installations

---

## Summary Statistics

**Total Features Implemented:** 28+ major features across 10 components

**Test Coverage:**
- IT-256, IT-254, IT-257, IT-262, IT-264, IT-277, IT-279, IT-281, IT-287, IT-291, IT-293, IT-294, IT-296, IT-300, IT-301, IT-302, IT-308, IT-310, IT-313, IT-317, IT-319
- AZUBI-403, AZUBI-421

**Quality Assurance References:**
- QS-97, QS-177, QS-187, QS-193, QS-218, QS-222, QS-227

**Bug Fixes:**
- INFO-1156, INFO-1157, INFO-1187, INFO-1188, INFO-1190, INFO-1192, INFO-1194, INFO-1196, INFO-1243

**Major Improvements:**
1. Enhanced stability and automatic recovery
2. New product launch (::LEA)
3. Better user feedback and error handling
4. Improved network and service management
5. Enhanced email and template functionality
6. Better multi-instance support
7. Modern socket technology for HL7 integration
