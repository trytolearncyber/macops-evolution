# 🏦 Nord Bank - Episode 02: The Logging Problem

**📖 Date:** Tuesday, 16 January, 10:00 AM  
**📍 Location:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Problem

**Compliance_Rassell** দ্রুত **NetMan_Khalid**-এর ডেস্কে এলেন।

> **Compliance_Rassell:**  
> "Khalid ভাই! Head Office থেকে নতুন Regulation! Transaction Log 90 Days রাখতে হবে!"

> **NetMan_Khalid:**  
> "90 Days? আগে তো 30 Days ছিল!"

> **Compliance_Rassell:**  
> "হ্যাঁ! Daily 50GB Log হয়! 90 Days মানে 4.5TB Storage দরকার!"

> **NetMan_Khalid:**  
> "এটা বড় Change! Proper Process Follow করতে হবে!"

---

# 🏢 Scene 2: The Meeting

> **NetMan_Khalid:**  
> "Team! Log 90 Days রাখতে হবে! Daily 50GB Log! Total 4.5TB Storage!"

> **SA_Asraf:**  
> "আমি সরাসরি Server বানাতে শুরু করতাম!"

> **DevOps_Taj:**  
> "Asraf ভাই! Random কাজ নয়! SDLC Process Follow করতে হবে!"

> **Infra_Babu:**  
> "SDLC কী?"

> **DevOps_Taj:**  
> "এটা একটা Standard Process। মোট 6টা Phase!"

---

# 💡 Scene 3: What is SDLC?

```text
═══════════════════════════════════════════════════════════════
SDLC - 6 PHASES
═══════════════════════════════════════════════════════════════

1️⃣ PLANNING
   └── Requirement বুঝতে হবে

2️⃣ DEFINE
   └── সব Document লিখতে হবে

3️⃣ DESIGN
   └── Architecture Design (HLD + LLD)

4️⃣ BUILD ⭐
   └── Infrastructure তৈরি

5️⃣ TEST ⭐
   └── Staging Environment-এ Test

6️⃣ DEPLOY ⭐
   └── Production Release

⭐ = Infrastructure DevOps Zone
```

> **SA_Asraf:**  
> "6টা Phase! আমি তো শুধু 2-3টা Phase করতাম!"

> **NetMan_Khalid:**  
> "বাদ পড়া Phase-ই পরে বড় Problem তৈরি করে!"

---

# 📋 Scene 4: Planning & Define

> **NetMan_Khalid:**  
> "Phase 1: Planning"

```text
═══════════════════════════════════════════════════════════════
PLANNING
═══════════════════════════════════════════════════════════════

Requirement
• 90 Days Log Retention

Daily Log
• 50GB

Total Storage
• 4.5TB

Affected Teams
• Firewall
• Application Server
• Database
```

> **Compliance_Rassell:**  
> "Requirement এখন একদম Clear!"

> **NetMan_Khalid:**  
> "Phase 2: Define"

```text
═══════════════════════════════════════════════════════════════
DEFINE (IRD)
═══════════════════════════════════════════════════════════════

Storage
• 4.5TB

Security
• Encryption

Access
• Only SOC Team
• Compliance Team

Retention
• 90 Days
• Auto Delete
```

---

# 🏗️ Scene 5: Design Phase

> **NetMan_Khalid:**  
> "Phase 3: Design"

```text
═══════════════════════════════════════════════════════════════
HLD (HIGH LEVEL DESIGN)
═══════════════════════════════════════════════════════════════

Firewall
      │
      ▼

Log Collection

      │
      ▼

Storage

      │
      ▼

Monitoring Dashboard
```

```text
═══════════════════════════════════════════════════════════════
LLD (LOW LEVEL DESIGN)
═══════════════════════════════════════════════════════════════

Storage
• 4.5TB
• Encrypted

Retention
• 90 Days

Access
• Write Permission

Dashboard
• Monitoring Tool
```

---

# 🔧 Scene 6: Build Phase

> **NetMan_Khalid:**  
> "Phase 4: Build। এখান থেকেই Infrastructure DevOps Zone শুরু।"

```text
═══════════════════════════════════════════════════════════════
BUILD
═══════════════════════════════════════════════════════════════

TOOLS

• Infrastructure Provisioning

• Configuration Management

• Version Control

────────────────────────────────────────────

STEPS

1. Infrastructure Configuration

2. Apply Configuration

3. Push Code
```

---

# 🧪 Scene 7: Test Phase

```text
═══════════════════════════════════════════════════════════════
TEST CHECKLIST
═══════════════════════════════════════════════════════════════

☐ Log আসছে?

☐ 90 Days Retention কাজ করছে?

☐ Dashboard কাজ করছে?

☐ Performance ঠিক আছে?

☐ Alert System কাজ করছে?
```

> **NOC_Jahid:**  
> "Log আসছে! Retention ঠিকমতো কাজ করছে!"

> **DevOps_Taj:**  
> "সব Test Pass ✅ Production-এর জন্য Ready!"

---

# 🚀 Scene 8: Deploy Phase

```text
═══════════════════════════════════════════════════════════════
DEPLOY
═══════════════════════════════════════════════════════════════

1. Infrastructure Apply

        │

        ▼

Resources Created

────────────────────────────────────────────

2. Configuration Run

        │

        ▼

Configuration Applied

────────────────────────────────────────────

3. Smoke Test

        │

        ▼

Passed ✅

────────────────────────────────────────────

4. Monitoring Enabled

        │

        ▼

Alerts Active

────────────────────────────────────────────

5. Compliance Sign-off

        │

        ▼

Production Ready ✅
```

> **Compliance_Rassell:**  
> "90 Days Retention Confirmed!"

---

# ✅ Scene 9: The Result

```text
═══════════════════════════════════════════════════════════════
BEFORE vs AFTER
═══════════════════════════════════════════════════════════════

BEFORE (No SDLC)

❌ Random Work

❌ Requirement Change
   → Rework

❌ Compliance Violation

────────────────────────────────────────────

AFTER (SDLC)

✅ Clear Requirement

✅ Proper Design

✅ Compliance Passed
```

> **NetMan_Khalid:**  
> "Centralized Logging System Ready! 90 Days Retention Active!"

---

# 🗣️ Interview Q&A

### Q1. SDLC কী?

**Answer**

SDLC (Software Development Life Cycle) হলো একটি 6-Phase Process।

- Planning
- Define
- Design
- Build
- Test
- Deploy

---

### Q2. Infrastructure DevOps Zone কোন Phase?

**Answer**

- Build
- Test
- Deploy

---

### Q3. HLD এবং LLD-এর পার্থক্য কী?

| HLD | LLD |
|------|------|
| High-Level Architecture | Detailed Technical Design |
| Overall System View | Component Details |
| Big Picture | Configuration Details |

---

### Q4. Planning বা Design Skip করলে কী হয়?

**Answer**

- Requirement ভুল হতে পারে
- Rework করতে হয়
- Compliance Risk তৈরি হয়

---

# 🎯 Self Introduction (MAC Matrix)

```text
1. Hello, আমি MAC Matrix।

2. আমি Infrastructure DevOps Engineer।

3. SDLC-এর 6টি Phase Follow করি।

4. Build, Test এবং Deploy Phase-এ কাজ করি।

5. Infrastructure Provision করি।

6. Security, Compliance এবং Audit Maintain করি।
```

---

# 📌 5 Easy Takeaways

```text
1. SDLC = 6 Phases

Planning
↓
Define
↓
Design
↓
Build
↓
Test
↓
Deploy

────────────────────────────

2. Infrastructure DevOps Zone

• Build
• Test
• Deploy

────────────────────────────

3. HLD

Architecture

LLD

Technical Details

────────────────────────────

4. Never Skip

Planning

Design

Otherwise

❌ Rework

❌ Compliance Risk

────────────────────────────

5. SDLC Makes Infrastructure

✔ Safe

✔ Repeatable

✔ Compliant
```

---

# 🛠️ Day 02 Tools: What to Use & What to Skip

```text
═══════════════════════════════════════════════════════════════
DAY 02 - TOOLS: USE ✅ vs SKIP ❌
═══════════════════════════════════════════════════════════════

✅ USE (Industry Standard)

1. Jira
   Work Tracking
   Agile Project Management

2. Confluence
   Documentation
   Knowledge Management

3. ServiceNow
   Incident & Change Management

────────────────────────────────────────────

❌ SKIP

1. Microsoft Project
   Traditional Project Tool

2. SharePoint
   Less Popular than Confluence

3. Asana
   Limited Enterprise Usage

4. Trello
   Less Powerful than Jira

5. Manual Documentation
   Use Version Control Instead

────────────────────────────────────────────

🔄 OPTIONAL (Advanced)

n8n

• Jira Ticket Automation

• Confluence Documentation Updates

• ServiceNow Incident Automation

• Slack & Email Notifications

• Automated Reporting

• Compliance Audit Workflow

• Change Request Approval
```

---

# 🧪 Labs

```text
═══════════════════════════════════════════════════════════════
LABS - DAY 02
═══════════════════════════════════════════════════════════════

LAB 01

Day02_01_SDLC_Phases

Task

Understand all 6 SDLC Phases

Output

SDLC Phases Summary

────────────────────────────────────────────

LAB 02

Day02_02_HLD_LLD_Design

Task

Understand the Difference Between
HLD and LLD

Output

Comparison Table

────────────────────────────────────────────

LAB 03

Day02_03_Infrastructure_Requirement_Document

Task

Create Nord Bank IRD

Output

Infrastructure Requirement Document

────────────────────────────────────────────

LAB 04

Day02_04_SDLC_Infrastructure_DevOps_Zone

Task

Understand Build, Test and Deploy

Output

Infrastructure DevOps Zone Summary
```

---

# 📖 Story Ending

> **NetMan_Khalid:**  
> "Requirement Clear হলে Project সফল হয়!"

> **DevOps_Taj:**  
> "Build-এর আগে Planning আর Design সবচেয়ে গুরুত্বপূর্ণ!"

> **Compliance_Rassell:**  
> "Compliance Pass! Audit Ready!"

```text
🎉 THE END 🎉

Follow SDLC

✔ Better Planning

✔ Better Documentation

✔ Better Infrastructure

✔ Better Compliance

✔ Better Delivery
```

---

# ➡️ Next Episode

## **Episode 03 - Virtualization Fundamentals**

> Learn how Virtualization, Hypervisors, Virtual Machines (VMs), Resource Allocation, VMware ESXi, and KVM help Nord Bank reduce hardware costs and improve infrastructure efficiency.