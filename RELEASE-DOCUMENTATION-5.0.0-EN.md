# infoskop-Base 5.0.0 - Complete Release Documentation

**Release Date**: September 2025
**Version**: 5.0.0
**Status**: Production Release

---

## Table of Contents

1. [Overview](#overview)
2. [infoskop-Base.exe](#infoskop-baseexe)
3. [infoskop-Monitor](#infoskop-monitor)
4. [infoskop::LEA (NEW)](#infoskoplea-new)
5. [Signexport.exe](#signexportexe)
6. [MediaServerStarter](#mediaserverstarter)
7. [VDDS-stage1.exe](#vdds-stage1exe)
8. [Starter.exe](#starterexe)
9. [HL7-Server](#hl7-server)
10. [Infoskop-Client.exe](#infoskop-clientexe)
11. [Updater & Full-Setup](#updater--full-setup)
12. [Testing Documentation](#testing-documentation)
13. [Migration Guide](#migration-guide)

---

## Overview

Version 5.0.0 is a major release with significant improvements across all components:

### Highlights
- **infoskop::LEA** - New product for service billing
- **Automatic Monitoring** - Starter.exe monitors and repairs automatically
- **Enhanced Service Management** - Support for multiple installations
- **Email Reliability** - Correct SMTP validation and status reporting
- **UX Improvements** - Loading indicators, icons, splash screen optimization
- **Online Function Control** - Consistent deactivation across all components
- **64-Bit Focus** - Only 64-bit and ARM64 architectures supported

### Breaking Changes
- **32-Bit Support Removed** - Only 64-bit systems are supported
- **Bonjour 32-Bit Removed** - Two new 64-bit installers (Intel/ARM)

---

## infoskop-Base.exe

### Bug Fixes

#### Email Send Status - SMTP Validation
**Ticket**: [INFO-1243](./details/info-1243.md) | [QS-227](./details/qs-227.md)

Fixed a critical bug where emails appeared to be sent successfully even though faulty SMTP server data was configured.

**Impact**:
- Correct validation of SMTP server data
- Authentication errors are detected and reported
- Actual send status is returned
- Prevents false user expectations

**Details**: [Full Documentation →](./details/info-1243.md)

---

## infoskop-Monitor

### New Features

#### 1. Flexible Image Resizing
Users can now flexibly adjust the size of embedded images in email and template texts.

**Features**:
- Drag & Drop images in WYSIWYG editor (CK5)
- Direct resizing in the editor
- Better design options for emails and templates

**Area**: WYSIWYG Editor | Email/Template Texts

---

### Bug Fixes

#### 2. Link Handling in Editor
**Ticket**: [QS-177](./details/qs-177.md)

Fixed a problem that prevented links in email and template texts, as well as in the form link builder, from opening in the local browser.

**Fixes**:
- Links open correctly in local browser
- Form link builder: Links must be clicked directly for preview
- Prevents unintentional opening

**Details**: [Full Documentation →](./details/qs-177.md)

---

#### 3. Price Transfer with Euro Symbol
**Ticket**: [QS-97](./details/qs-97.md)

Price transfer in PA and Bleaching cockpit now works correctly when the price contains a Euro symbol (€).

**Affected Areas**:
- PA-Cockpit
- Bleaching-Cockpit

**Details**: [Full Documentation →](./details/qs-97.md)

---

#### 4. infoskop::ORA License
**Ticket**: [INFO-1194](./details/info-1194.md)

Fixed an error in querying the infoskop::ORA license.

**Impact**:
- ::ORA customers can use licensed features
- Response function is correctly enabled
- Consistent license verification

**Details**: [Full Documentation →](./details/info-1194.md)

---

### Adjustments

#### 5. Cockpit Icons Updated
**Ticket**: [QS-222](./details/qs-222.md)

Missing icons in the cockpits have been added and updated.

**Improvements**:
- Modernized icon design
- Consistent presentation
- Better recognition of functions

**Details**: [Full Documentation →](./details/qs-222.md)

---

#### 6. Offline Displays Optimized
**Tickets**: [QS-187](./details/qs-187.md) | [AZUBI-403](./details/azubi-403.md) | [AZUBI-421](./details/azubi-421.md)

Displays when online function is deactivated have been comprehensively revised.

**Improvements**:
- Online form settings are correctly hidden
- Email sending is blocked system-wide when deactivated
- Consistent behavior in infoskop-Base, Monitor and App
- Clear user guidance

**Related Testing**: [IT-277 Test Case](./details/it-277.md)

**Details**:
- [QS-187 - Offline Displays](./details/qs-187.md)
- [AZUBI-403 - Access to Online Form Settings](./details/azubi-403.md)
- [AZUBI-421 - Email Sending When Deactivated](./details/azubi-421.md)

---

#### 7. Response Function
The response function is only active for ::ORA customers. For other users, the display has been adjusted and the function deactivated.

**License-based Activation**:
- Only ::ORA license: Function active
- Without ::ORA license: Function deactivated and hidden

---

### Optimizations

#### 8. Bulk Edit Warning Settings
**Ticket**: [AZUBI-399](./details/azubi-399.md)

The display behavior of bulk editing in warning settings has been improved.

**Fixes**:
- Consistent display when switching between tabs
- Correct synchronization with "All Yes/No" option
- No more inconsistent display states

**Details**: [Full Documentation →](./details/azubi-399.md)

---

#### 9. Patient Data Deletion Optimized
**Ticket**: AZUBI-401

The process of deleting patient data in the Monitor has been adjusted and optimized.

**Improvements**:
- Faster deletion process
- Better feedback to users
- Correct validation before deletion

---

## infoskop::LEA (NEW)

**New Product as of Version 5.0.0**

### Integration and Functions

#### 1. Webframe for Client
Integration of the new webframe for the client

**Features**:
- Independent Windows window instance
- Integration in infoskop-Client.exe
- Modern web-based interface

---

#### 2. Base Management
Functions in the Base for managing requests and data storage

**Functionality**:
- Request management
- Data persistence
- API for client communication

---

#### 3. Automatic Licensing
Automatic activation of the license when the service catalog is correctly configured

**License Model**:
- Automatic detection of ::LEA license
- Activation without manual intervention
- Dependent on service catalog configuration

---

## Signexport.exe

### Optimizations

#### 1. Proxy Configuration
Option added to configure a proxy.

**Use Case**:
- Corporate networks with proxy servers
- Configurable proxy settings
- Support for authenticated proxies

---

## MediaServerStarter

### Optimizations

#### 1. Service Installation Fixed
**Ticket**: [INFO-1157](./details/info-1157.md)

The installation of MediaServerStarter as a service has been improved. A serious error that led to unreadable service names in Windows has been fixed.

**Fixes**:
- Service names are correctly readable
- Windows Service Manager can manage the service
- Support for multiple installations

**Details**: [Full Documentation →](./details/info-1157.md)

---

#### 2. Service Management
The MediaServerStarter now saves service names in the Base-Config to clearly identify multiple installations.

**Configuration Parameters**:
```ini
[Server]
mname = Name of the MediaServer service
```

**Advantages**:
- Unique identification with multiple MediaServers
- Correct management by Updater
- Later versions can identify the service

---

## VDDS-stage1.exe

### Bug Fixes

#### 1. Evident Configuration
**Tickets**: [INFO-1190](./details/info-1190.md) | [QS-218](./details/qs-218.md)

Fixed an error that prevented automatic Evident configuration from being recognized correctly.

**Fixes**:
- Automatic configuration detection works
- Evident parameters are correctly read
- Data synchronization with Evident runs reliably
- Reduced configuration effort

**Details**: [Full Documentation →](./details/info-1190.md)

---

## Starter.exe

### New Features

#### 1. Automatic Self-Monitoring
**Ticket**: [INFO-1187](./details/info-1187.md)

The Starter.exe now automatically monitors the functionality of the TCP socket server of infoskop-Base.exe and restarts the application if problems occur.

**Features**:
- **Default: ON** - Activated by default
- **Adaptive Timeouts** - Increase automatically on repeated restarts
- **Intelligent Logic** - Allows lengthy actions to succeed
- **Extended Logging** - report.dat + Logcheck integration

**Configuration** (Base-config):
```ini
[server]
restartWhenUnresponsive = 1          # 1=ON, 0=OFF
lifesignToBaseInterval = 5000         # Check interval (ms)
lifesignRestartBusyBaseAfterInterval = 30000  # Timeout before restart (ms, increases automatically)
```

**Details**: [Full Documentation →](./details/info-1187.md)

---

### Optimizations

#### 2. Service Management
The Starter saves service names in the Base-Config to uniquely identify multiple installations.

**Configuration Parameters**:
```ini
[Server]
bname = Name of the infoskop-Base service
mname = Name of the MediaServer service
```

---

#### 3. Error Logging
In case of error, the Starter logs its attempts to reach the Base in `report.dat`.

**Features**:
- Detailed connection logs
- Automatic Logcheck integration
- Better diagnosis of problems

---

#### 4. HL7 Server Monitoring
HL7 servers are now automatically monitored. When the Base Starter is shut down, the HL7 server closes its service "gracefully", avoiding network problems and long timeouts.

**Configuration** (Base-config):
```ini
[hl7]
smartHandling = 0          # 1=ON (requires hl7/enabled=1)
waitforclose = 6000        # Wait time for graceful shutdown (ms)
```

**Advantages**:
- No more network timeouts
- Proper closing of socket server
- Avoidance of port blocking

**See also**: [HL7-Server - Graceful Shutdown](#hl7-server)

---

#### 5. Service Installation Fixed
**Ticket**: [INFO-1156](./details/info-1156.md)

Optimizations for installation as a service, fixes an error where installed service names were corrupt and not readable by Windows.

**Details**: [Full Documentation →](./details/info-1156.md)

---

## HL7-Server

### Optimizations

#### 1. Socket Server - Graceful Shutdown
Now enables graceful shutdown of the socket server (in conjunction with Starter.exe).

**Configuration** (HL7-Server config):
```ini
[server]
useChilkatSockets = 0  # 1=ON (prerequisite for graceful shutdown)
                       # Activated automatically when module/orbis=1 and server/openstream=1
```

**Technical Details**:
- Switch from old sockets to newer Chilkat sockets
- More options and control
- Clean shutdown without network timeouts

**Prerequisite**: `server/useChilkatSockets=1` must be enabled

---

## Infoskop-Client.exe

### New Features

#### 1. ::LEA Support
Support for the new product infoskop::LEA implemented.

**Features**:
- Launch Windows application as independent window instance
- Query license from infoskop-Base.exe
- Integration into existing client interface

---

### Optimizations

#### 2. Webframe Loading Display
**Ticket**: [INFO-1196](./details/info-1196.md)

For longer loading times of webframes (infoskop-Monitor and ::LEA), users now receive a "Please wait..." display.

**Improvements**:
- Transparent feedback during loading process
- Professional user experience
- Prevents confusion during longer loading times
- Disappears automatically after successful loading

**Details**: [Full Documentation →](./details/info-1196.md)

---

### Bug Fixes

#### 3. Splash Display Deduplication
**Tickets**: [INFO-1192](./details/info-1192.md) | [QS-193](./details/qs-193.md)

Fixed a problem where multiple identical splash displays could be loaded simultaneously in Z1.

**Fix**:
- Only one display per execution
- Singleton pattern implemented
- Resource optimization
- Clean user interface

**Details**: [Full Documentation →](./details/info-1192.md)

**Related Testing**: [IT-257 Test Case](./details/it-257.md)

---

## Updater & Full-Setup

### Adjustments

#### 1. Bonjour 32Bit Removed
**Ticket**: [INFO-1188](./details/info-1188.md)

The installation file for Bonjour 32Bit has been removed. The product now only supports 64-bit and ARM systems.

**Changes**:
- Bonjour 32-bit removed
- Two 64-bit installers added (Intel/ARM)
- Both can be installed in parallel
- Automatic architecture detection

**Compatibility**:
- Windows 10/11 (64-bit)
- Windows Server 2016/2019/2022 (64-bit)
- ARM64-based Windows devices
- 32-bit systems no longer supported

**Details**: [Full Documentation →](./details/info-1188.md)

---

#### 2. Service Naming
For installations with multiple Bases on one machine, the standard service name "infoskop-Base" is no longer automatically assigned to avoid conflicts.

**Behavior**:
- **Without `/MULTIPLEBASES` flag**: Standard name "infoskop-Base"
- **With `/MULTIPLEBASES` flag**: Individual name required

---

### Optimizations

#### 3. Individual Service Names
The Updater can now accept individual service names for Base and MediaServer to correctly stop and restart them.

**Parameters**:
```cmd
infoskop-Base-Updater.exe /bname "infoskop-Base-Practice1" /mname "MediaServer-Practice1"
```

**Advantages**:
- Correct service management for multiple installations
- Updater can control specific services
- No manual intervention required

**See also**:
- [INFO-1156 - Starter Service Installation](./details/info-1156.md)
- [INFO-1157 - MediaServerStarter Service Installation](./details/info-1157.md)

---

## Testing Documentation

Comprehensive test cases are available for critical features:

### Test Cases

#### IT-257: Base Updater - Manual Update Process
**[View Test Case →](./details/it-257.md)**

Validation of the manual update process via infoskop-Monitor, including:
- Splash displays during update
- Version verification
- Automatic client start

**Coverage**:
- Update management
- Splash displays (only one per execution)
- Version management

---

#### IT-277: Online Functions Deactivation
**[View Test Case →](./details/it-277.md)**

Comprehensive validation of deactivating all online functions.

**Coverage**:
- Online forms (Forms, Templates, System Templates, Encryption)
- Email functionality (Patients, Inbox/Outbox, Documents)
- Evaluations (PA-Cockpit, Bleaching-Cockpit)
- Stage1
- Re-activation and restoration

**Related Tickets**:
- [AZUBI-403](./details/azubi-403.md)
- [AZUBI-421](./details/azubi-421.md)
- [QS-187](./details/qs-187.md)

---

## Migration Guide

### From Version 4.x to 5.0.0

#### System Requirements

**Check BEFORE updating**:
1. System is 64-bit (Windows 10/11 or Server 2016+)
2. 32-bit systems are NOT supported anymore
3. Sufficient disk space (at least 2 GB free)
4. Admin rights for installation

---

#### Automatic Update (recommended)

Via infoskop-Monitor:
1. Open infoskop-Monitor
2. Navigate to **Administration** → **infoskop-Base Update**
3. Click **"UPDATE MANUALLY DEPOSIT"**
4. Select `infoskop-Base-5.0.0-Updater.exe`
5. Confirm the update process
6. Wait for splash displays:
   - "Updates for infoskop-Base have been started"
   - "Updates completed"

**Details**: [IT-257 Test Case](./details/it-257.md)

---

#### Manual Installation

For network deployments or multiple systems:
```cmd
# Standard installation
infoskop-Base-5.0.0-Updater.exe

# Multiple installation with individual service names
infoskop-Base-5.0.0-Updater.exe /MULTIPLEBASES /bname "infoskop-Base-Practice1" /mname "MediaServer-Practice1"
```

---

#### After the Update

**Checks**:
1. Check version (should be 5.0.0)
2. Services running:
   - infoskop-Base (or individual name)
   - MediaServerStarter (if used)
   - HL7-Server (if used)
3. Bonjour service running
4. Licenses are correct:
   - ::ORA license (if available)
   - ::LEA license (with service catalog)

**Test new features**:
- [ ] Automatic Starter monitoring (runs in background)
- [ ] ::LEA (if licensed)
- [ ] Webframe loading display
- [ ] Online functions deactivation

---

#### Troubleshooting

**Problem**: Update fails

**Solution**:
1. Check services (stop all before update)
2. Check admin rights
3. Check disk space
4. Check log files (`report.dat`, Logcheck)

---

**Problem**: Bonjour not working

**Solution**:
1. Open `services.msc`
2. Look for "Bonjour Service"
3. Start the service
4. Set startup type to "Automatic"

**Details**: [INFO-1188 - Bonjour](./details/info-1188.md)

---

**Problem**: Services won't start

**Solution**:
1. Check service names in Base-Config:
   ```ini
   [Server]
   bname = <Your service name>
   mname = <MediaServer service name>
   ```
2. Adjust Updater parameters (`/bname`, `/mname`)
3. Check Windows Event Log

**Details**: [INFO-1156 - Service Installation](./details/info-1156.md)

---

## Support & Feedback

### Documentation Structure

All detailed documentation is organized in the `details/` folder:
- **AZUBI-xxx.md**: Training/Apprenticeship issues
- **QS-xxx.md**: Quality Assurance tickets
- **IT-xxx.md**: Test cases with detailed steps
- **INFO-xxx.md**: Information/General issues

### Quick Reference

| Component | Key Tickets | Documentation |
|-----------|-------------|---------------|
| infoskop-Base.exe | INFO-1243, QS-227 | Email SMTP Validation |
| infoskop-Monitor | AZUBI-403, AZUBI-421, QS-187 | Online Functions Control |
| infoskop::LEA | NEW in 5.0.0 | New Product |
| Starter.exe | INFO-1187, INFO-1156 | Auto-Monitoring, Service Installation |
| MediaServerStarter | INFO-1157 | Service Installation |
| VDDS-stage1.exe | INFO-1190, QS-218 | Evident Configuration |
| Infoskop-Client.exe | INFO-1192, INFO-1196, QS-193 | Splash Screens, Loading Display |
| Updater/Setup | INFO-1188 | Bonjour 64-Bit |

### Test Cases

| Test Case | Purpose | Documentation |
|-----------|---------|---------------|
| IT-257 | Update Process | [View](./details/it-257.md) |
| IT-277 | Online Functions Deactivation | [View](./details/it-277.md) |

---

## Release Notes by Audience

For target group-specific release notes, see:
- **[TECHNIK](./release-notes-5.0.0-TECHNIK.md)** - Technical details & configuration
- **[SUPPORT](./release-notes-5.0.0-SUPPORT.md)** - Support notes, troubleshooting
- **[VERTRIEB](./release-notes-5.0.0-VERTRIEB.md)** - Sales arguments
- **[KUNDEN](./release-notes-5.0.0-KUNDEN.md)** - User benefits, new features
- **[TRAINING](./release-notes-5.0.0-TRAINING.md)** - Training focus

---

**Document Version**: 1.0
**Last Updated**: November 2025
**Maintained by**: infoskop Development Team

---

© 2025 synmedico | infoskop-Base Version 5.0.0
