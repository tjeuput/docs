# Documentation Structure Summary for Version 5.0.0

This document explains the relationship between all documentation files in this repository and how they connect to each other.

---

## 📋 File Types Overview

### 1. **ReleaseNote.md** (Main Release Notes)
**Purpose**: Customer-facing release notes listing all changes in version 5.0.0

**Structure**: Organized by component/executable:
- Infoskop-Base.exe
- Infoskop-Monitor
- Infoskop::LEA
- Signexport.exe
- MediaServerStarter
- VDDS-stage1.exe
- Starter.exe
- HL7-Server
- Infoskop-Client.exe
- Infoskop-Base-Updater

Each bullet point references one or more ticket IDs (INFO-*, AZUBI-*, etc.)

---

### 2. **IT-*.csv Files** (Test Steps - CSV Format)
**Purpose**: Simple test execution steps in CSV format

**Structure**:
```
Action, Data, Expected Result
[Step 1], [Input data], [Expected outcome]
[Step 2], [Input data], [Expected outcome]
...
```

**Use Case**: Quick reference for testers to execute test cases

**Example**: IT-262.csv contains steps to test QR-Code opening in Postausgang

---

### 3. **IT-*.xml Files** (JIRA Export - Metadata)
**Purpose**: Complete JIRA ticket metadata export from the testing system

**Contains**:
- Full ticket description (HTML formatted)
- Links to related tickets
- Status information
- Reporter/Assignee details
- Creation/update dates
- Custom fields and metadata

**Use Case**: Complete audit trail and ticket relationships from JIRA

---

### 4. **IT-*.md Files** (Test Cases - Detailed Documentation)
**Location**: `/details/it-*.md`

**Purpose**: Comprehensive test case documentation

**Structure**:
- Test Category
- Purpose/Description
- Prerequisites
- Detailed test steps (table format)
- Expected results
- Related tickets
- Coverage information
- Test result status

**Use Case**: Detailed testing documentation with full context

---

### 5. **Bug/Feature Detail Files** (INFO-*, AZUBI-*, QS-* in `/details/`)
**Purpose**: Detailed documentation for each bug fix or feature

**Structure**:
- Category (Bug Fix, Feature, etc.)
- Status (Done/In Progress/Released)
- Problem description
- Solution description
- Related tickets
- Technical details
- Before/After comparison
- User benefits
- Testing references

**Use Case**: Complete understanding of what was fixed/added and why

---

### 6. **Customer-Facing Docs** (`/customer-docs/*.md`)
**Purpose**: User-friendly, marketing-style descriptions of features

**Structure**:
- Friendly title with emoji
- "What was improved?" section
- Practical examples (Before/After)
- User benefits
- Simple, non-technical language

**Use Case**: External communication, user guides, "What's New" documentation

---

## 🔗 How They Connect: Example Flow

### Example: Bug AZUBI-403 (Online Functions Access Issue)

```
┌─────────────────────────────────────────────────────────────────┐
│                     ReleaseNote.md                              │
│  Line 19: "Anzeigen bei deaktivierter Onlinefunktion           │
│            angepasst (AZUBI-403, AZUBI-421)"                    │
└────────────────┬────────────────────────────────────────────────┘
                 │
                 ├──────────────────────────────────────────────┐
                 │                                              │
                 v                                              v
┌────────────────────────────────┐        ┌──────────────────────────────┐
│  details/azubi-403.md          │        │  details/azubi-421.md        │
│  ─────────────────────────     │        │  ───────────────────────     │
│  ■ Full bug description        │        │  ■ Related bug               │
│  ■ Reproduction steps          │◄───────┤  ■ Also fixed                │
│  ■ Solution implemented        │relates │  ■ References AZUBI-403      │
│  ■ User benefit                │        │                              │
│  ■ References to tests ──┐     │        └──────────────────────────────┘
└──────────────────────────┼─────┘
                           │
                           v
         ┌─────────────────────────────────────┐
         │  details/it-277.md (Test Case)      │
         │  ────────────────────────────────   │
         │  ■ Test Category                    │
         │  ■ Purpose: Test offline mode       │
         │  ■ 17 detailed test steps           │
         │  ■ Expected results                 │
         │  ■ References AZUBI-403, AZUBI-421  │
         └──────┬────────────────┬──────────────┘
                │                │
                │                │
                v                v
   ┌────────────────────┐   ┌────────────────────┐
   │  IT-277.csv        │   │  IT-277.xml        │
   │  (Quick reference) │   │  (JIRA metadata)   │
   │  ──────────────    │   │  ───────────────   │
   │  ■ 18 test steps   │   │  ■ Ticket status   │
   │  ■ CSV format      │   │  ■ Links           │
   │  ■ Easy execution  │   │  ■ Assignee info   │
   └────────────────────┘   └────────────────────┘
                │
                │
                v
   ┌──────────────────────────────────┐
   │  customer-docs/offline-mode.md   │
   │  ─────────────────────────────   │
   │  ■ User-friendly language        │
   │  ■ "What was improved?"          │
   │  ■ Before/After examples         │
   │  ■ Benefits for end users        │
   │  ■ Emojis and simple formatting  │
   └──────────────────────────────────┘
```

---

## 📊 Relationship Matrix

| Ticket Type | Where to Find | What It Contains | Links To |
|-------------|---------------|------------------|----------|
| **Bug ID** (INFO-*, AZUBI-*) | `details/[id].md` | Bug description, solution, impact | IT-* tests, QS-* tickets |
| **Test Case** (IT-*) | `details/it-*.md` + `.csv` + `.xml` | Test steps, expected results | Bug tickets, QS tickets |
| **Quality Check** (QS-*) | `details/qs-*.md` | Quality assurance validation | Bug tickets, IT tests |
| **Feature** | `customer-docs/*.md` | User-friendly description | Related bugs/tests |
| **Release Notes** | `ReleaseNote.md` | All changes summary | All ticket IDs |

---

## 🎯 Answering Your Questions

### "If there is a bug, what is the solution?"

**Steps**:
1. Find the bug ID in `ReleaseNote.md` (e.g., AZUBI-403)
2. Open `details/azubi-403.md`
3. Read the **"Lösung"** (Solution) section
4. See the **"Beschreibung"** for the original problem

**Example**: AZUBI-403
- **Problem**: Settings accessible when online functions disabled
- **Solution**: UI adjusted to hide/disable all online-related settings when offline
- **Agreement**: Documented in the ticket as "Anzeigen angepasst"

---

### "Which test validates the fix?"

**Steps**:
1. In the bug detail file (e.g., `details/azubi-403.md`)
2. Look for **"Zugehörige Tickets"** or **"Testing"** section
3. Find the IT-* reference (e.g., IT-277)
4. Open `details/it-277.md` for detailed test steps
5. Use `IT-277.csv` for quick execution
6. Check `IT-277.xml` for JIRA metadata

**Example**: AZUBI-403
- **Test**: IT-277
- **Steps**: 17 detailed steps testing all offline scenarios
- **Result**: ✅ PASS

---

### "For a new feature, what was before and what changed?"

**Steps**:
1. Find feature in `ReleaseNote.md`
2. Open the referenced ticket in `details/`
3. Look for **"Vorher vs. Nachher"** or **"Beschreibung"** section
4. Check customer docs in `customer-docs/` for user-friendly comparison

**Example**: INFO-1192 (Splash Screen Bug)
- **Before**: Multiple identical splash screens appeared
- **After**: Only one splash screen per execution
- **How**: Singleton pattern implementation
- **User Benefit**: Clearer UI, better performance

---

## 📁 File Organization

```
/docs/
├── ReleaseNote.md                    # Main release notes
│
├── IT-*.csv                          # Test steps (CSV)
├── IT-*.xml                          # Test metadata (JIRA)
│
├── details/
│   ├── azubi-*.md                    # Bug fixes (AZUBI project)
│   ├── info-*.md                     # Bug fixes (INFO project)
│   ├── it-*.md                       # Test cases (detailed)
│   └── qs-*.md                       # Quality assurance tickets
│
└── customer-docs/
    ├── cockpit-icons.md              # Feature: Icon fixes
    ├── auto-monitoring.md            # Feature: Auto monitoring
    ├── evident-integration.md        # Feature: Evident config
    ├── email-reliability.md          # Feature: Email validation
    ├── offline-mode.md               # Feature: Offline UI
    ├── online-functions-control.md   # Feature: Online controls
    ├── link-handling.md              # Feature: Link fixes
    └── lea.md                        # Feature: LEA integration
```

---

## 🔍 Quick Reference Guide

### To understand a specific bug:
```
ReleaseNote.md (find ticket ID)
    → details/[ticket-id].md (read full description)
        → See "Lösung" section for fix
        → See "Testing" for validation
```

### To execute a test:
```
details/it-*.md (understand context)
    → IT-*.csv (execute steps)
    → IT-*.xml (check JIRA status/links)
```

### To explain to customers:
```
ReleaseNote.md (find feature)
    → customer-docs/*.md (get user-friendly explanation)
```

### To trace a complete feature:
```
ReleaseNote.md (ticket ID)
    → details/[bug-id].md (technical details)
    → details/it-*.md (test validation)
    → customer-docs/*.md (customer explanation)
```

---

## 💡 Summary

This documentation system provides **4 levels of detail**:

1. **ReleaseNote.md**: High-level summary for all users
2. **IT-*.csv**: Quick test execution reference
3. **details/*.md**: Detailed technical documentation
4. **customer-docs/*.md**: User-friendly feature explanations

Each level links to the others, creating a complete documentation ecosystem that serves developers, testers, and end users.
