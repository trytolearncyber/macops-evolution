# 🏦 Nord Bank - Episode 02: The Logging Crisis

**📖 তারিখ:** Tuesday, 16 January, 10:00 AM  
**📍 স্থান:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Compliance Call

Compliance_Rassell দ্রুত NetMan_Khalid-এর ডেস্কে এলেন। হাতে একটি ফাইল।

**Compliance_Rassell:**

> "Khalid ভাই। Head Office থেকে নতুন Regulation এসেছে। Banking Authority বলছে—আমাদের সব transaction log 90 days ধরে রাখতে হবে। আগে ছিল 30 days।"

**NetMan_Khalid:**

> "90 days? Current system কত দিন রাখে?"

**Compliance_Rassell:**

> "বর্তমানে 30 days। নতুন Regulation মানতে হলে infrastructure change করতে হবে।"

**NetMan_Khalid:**

> "এটা কত বড় change?"

**Compliance_Rassell:**

> "এই change-এ Firewall, App Server, Database—সব log দেবে। Daily incoming log 50GB। 90 days মানে 4.5TB storage দরকার।"

**NetMan_Khalid:**

> "4.5TB। এটা ছোট change না। Process follow করতে হবে।"

NetMan_Khalid দ্রুত মিটিং ডাকলেন।

---

# 🏢 Scene 2: The Meeting

Meeting room-এ সবাই উপস্থিত:

- NetMan_Khalid *(Infrastructure DevOps)*
- Compliance_Rassell *(Compliance Lead)*
- Infra_Babu *(Infrastructure Architect)*
- DevOps_Taj *(DevOps Engineer)*
- SA_Asraf *(System Administrator)*
- Security_Shahed *(Security Specialist)*
- NOC_Jahid *(NOC Lead)*
- Audit_Mahfuz *(Audit Lead)*

**NetMan_Khalid:**

> "Team। নতুন Regulation—transaction log 90 days রাখতে হবে। Daily 50GB log। Total 4.5TB storage দরকার।"

**Infra_Babu:**

> "বড় change। নতুন storage system লাগবে। কিন্তু আমরা কিভাবে start করব?"

**SA_Asraf:**

> "আমি তো সরাসরি server বানাতে শুরু করতাম।"

**DevOps_Taj:**

> "Asraf vai। আমরা Infrastructure DevOps engineer। আমরা SDLC follow করি। First Planning।"

**NetMan_Khalid:**

> "ঠিক বলেছে Taj vai। SDLC-র 6টা Phase আছে। চলুন শুরু করি Planning থেকে।"

---

# 📋 Scene 3: Planning & Requirements Phase

NetMan_Khalid whiteboard-এ লিখলেন:

```text
═══════════════════════════════════════════════════════════════
PHASE 1: PLANNING & REQUIREMENTS
═══════════════════════════════════════════════════════════════

কী করতে হবে:
├── Business Requirement বুঝতে হবে
├── কারা affected—সেটা বের করতে হবে
└── Data পরিমাণ Estimate করতে হবে

Nord Bank-এর উদাহরণ:
├── Requirement: 90 days log retention
├── Affected Teams:
│   ├── Firewall Team (FortiGate log দেবে)
│   ├── App Server Team (Application log দেবে)
│   └── Database Team (DB log দেবে)
├── Daily Log: 50GB
└── Total Storage: 50GB × 90 = 4.5TB
```

**Compliance_Rassell:**

> "আমাদের requirement clear। 90 days retention। Daily 50GB।"

**DevOps_Taj:**

> "Storage estimate done। এখন cost estimate করতে হবে।"

**NetMan_Khalid:**

> "Planning Phase-এর Output—Requirement List। সব requirement list করে ফেলি।"

**NOC_Jahid:**

> "আমাদের NOC team-কে log monitoring করতে হবে।"

**Security_Shahed:**

> "Encryption mandatory। KMS use করতে হবে।"

**Audit_Mahfuz:**

> "Audit trail রাখতে হবে। কে কোন log দেখছে—সেটা log করতে হবে।"

**NetMan_Khalid:**

> "সব requirement note করে ফেলি।"

---

# 📝 Scene 4: Define Phase

**NetMan_Khalid:**

> "এখন Define Phase। সব requirement Document-এ লিখতে হবে।"

**Infra_Babu:**

> "Infrastructure Requirement Document (IRD) তৈরি করি।"

```text
═══════════════════════════════════════════════════════════════
PHASE 2: DEFINE
═══════════════════════════════════════════════════════════════

কী করতে হবে:
├── সব Requirement Document-এ লিখতে হবে
├── Storage Size উল্লেখ করতে হবে
├── Retention Period উল্লেখ করতে হবে
└── Access Control উল্লেখ করতে হবে

Nord Bank-এর IRD:
───────────────────────────────────────────────────────────────
INFRASTRUCTURE REQUIREMENT DOCUMENT

Project: Centralized Logging System
Requirement: 90 days transaction log retention

Storage:
├── Daily Log: 50GB
├── Total Storage: 4.5TB
└── Storage Type: S3 (Long-term) + CloudWatch Logs (Real-time)

Security:
├── Encryption: AWS KMS
├── Access: Only SOC Team + Compliance Team
└── Audit: CloudTrail enabled

Retention Policy:
├── 1-30 days: CloudWatch Logs (Real-time access)
├── 31-90 days: S3 (Cost-effective storage)
└── After 90 days: Auto-delete
───────────────────────────────────────────────────────────────
```

**Compliance_Rassell:**

> "Perfect। এই Document-এ সব requirement আছে।"

**Audit_Mahfuz:**

> "Audit trail requirement added। ভালো।"

---

# 🏗️ Scene 5: Design Phase (HLD + LLD)

**NetMan_Khalid:**

> "এখন Design Phase। HLD আর LLD করতে হবে।"

**DevOps_Taj:**

> "HLD দিয়ে start করি—High-Level Design।"

```text
═══════════════════════════════════════════════════════════════
PHASE 3: DESIGN (HLD + LLD)
═══════════════════════════════════════════════════════════════

HIGH-LEVEL DESIGN (HLD):
═══════════════════════════════════════════════════════════════

Centralized Log System Architecture

  ┌─────────────┐
  │  FortiGate  │──Log──┐
  │  Firewall   │       │
  └─────────────┘       │
                        ▼
  ┌─────────────┐  ┌─────────────┐
  │ App Server  │──│ CloudWatch  │
  │ (Dell R750) │  │   Logs      │
  └─────────────┘  └─────────────┘
                        │
  ┌─────────────┐       │
  │  Database   │──Log──┘
  └─────────────┘       │
                        ▼
                  ┌─────────────┐
                  │  S3 Bucket  │
                  │ (4.5TB)     │
                  └─────────────┘
                        │
                        ▼
                  ┌─────────────┐
                  │  Grafana    │
                  │ Dashboard   │
                  └─────────────┘

LOW-LEVEL DESIGN (LLD)
═══════════════════════════════════════════════════════════════

AWS Resources Details:

1. S3 Bucket: nord-bank-logs-production
   ├── Lifecycle: 90 days → Delete
   ├── Encryption: KMS (alias/nord-bank-logs-key)
   └── Versioning: Disabled

2. CloudWatch Log Group
   ├── Retention: 90 days
   └── Metric Filter: Error Alert

3. IAM Role: log-writer-role
   ├── S3 PutObject
   ├── CloudWatch PutLogEvents
   └── KMS Encrypt

4. EC2 (Grafana)
   ├── t3.medium
   └── Port 3000 (VPN Only)

5. VPC
   ├── Private Subnet
   └── Flow Logs Enabled
```

**Security_Shahed:**

> "Security Design ভালো। KMS encryption, private subnet—সব আছে।"

**Infra_Babu:**

> "LLD clear। এই Design নিয়ে কাজ করা সহজ হবে।"

---

# 🔧 Scene 6: Build Phase

**NetMan_Khalid:**

> "এখন Build Phase। Infrastructure DevOps Zone শুরু হয়।"

**DevOps_Taj:**

> "এখন Terraform আর Ansible দিয়ে সব create করব।"

```text
═══════════════════════════════════════════════════════════════
PHASE 4: BUILD (Infrastructure DevOps Zone)
═══════════════════════════════════════════════════════════════

Terraform
├── S3
├── CloudWatch
├── IAM
└── EC2

Ansible
├── Grafana Install
├── Filebeat Install
└── Security Hardening

GitHub
├── Code Review
├── Pull Request
└── Merge to Main
```

**SA_Asraf:**

> "আমি তো manual-এ server বানাতাম। এখানে code দিয়ে সব হচ্ছে!"

**DevOps_Taj:**

> "Infrastructure as Code। সব Code-এ লেখা।"

**Infra_Babu:**

> "Build Phase-এর Output—Infrastructure Ready।"

---

# 🧪 Scene 7: Test Phase

**NetMan_Khalid:**

> "Build শেষ। এখন Test Phase।"

```text
═══════════════════════════════════════════════════════════════
PHASE 5: TEST
═══════════════════════════════════════════════════════════════

Test Checklist

□ FortiGate Logs
□ App Server Logs
□ Database Logs
□ CloudWatch Logs
□ S3 Storage
□ 90 Days Retention
□ Grafana Dashboard
□ Performance
□ Alert System
```

**NOC_Jahid:**

> "Log আসছে। Monitoring ঠিক আছে।"

**Security_Shahed:**

> "Encryption enabled।"

**Compliance_Rassell:**

> "Compliance verified।"

**DevOps_Taj:**

> "All Test Passed ✅"

```text
TEST REPORT

Log Ingestion      ✅ PASSED
Retention          ✅ PASSED
Storage            ✅ PASSED
Dashboard          ✅ PASSED
Security           ✅ PASSED
Performance        ✅ PASSED

Overall Status:
✅ READY FOR PRODUCTION
```

---

# 🚀 Scene 8: Deploy Phase

**NetMan_Khalid:**

> "Production Deploy শুরু।"

```text
═══════════════════════════════════════════════════════════════
PHASE 6: DEPLOY
═══════════════════════════════════════════════════════════════

1. Terraform Apply
2. Ansible Playbook
3. Smoke Test
4. Enable Monitoring
5. Compliance Sign-off
6. Documentation Update
```

**NOC_Jahid:**

> "Production healthy।"

**Compliance_Rassell:**

> "Compliance confirmed।"

**Audit_Mahfuz:**

> "Audit trail complete।"

---

# 💡 Scene 9: The Impact

**NetMan_Khalid:**

> "Centralized Logging System ready।"

**Compliance_Rassell:**

> "Compliance pending আর নেই।"

**Infra_Babu:**

> "Planning → Define → Design → Build → Test → Deploy। সব Phase complete।"

**SA_Asraf:**

> "Planning আর Design কতটা গুরুত্বপূর্ণ আজ বুঝলাম।"

**DevOps_Taj:**

> "Build, Test, Deploy—Automation দিয়ে 10 days-এর কাজ 1 day।"

**Finance_Arif:**

> "Storage cost optimized।"

**Audit_Mahfuz:**

> "Everything documented।"

---

# 📖 Scene 10: The Lesson

**SA_Asraf:**

> "15 years manual process করেছি। SDLC-এর গুরুত্ব আজ বুঝলাম।"

```text
═══════════════════════════════════════════════════════════════
SDLC - KEY LEARNINGS
═══════════════════════════════════════════════════════════════

1. Planning
2. Define
3. Design (HLD + LLD)
4. Build ⭐
5. Test ⭐
6. Deploy ⭐

⭐ Infrastructure DevOps Zone

OLD:
Build First

NEW:
Planning → Define → Design → Build → Test → Deploy
```

**Infra_Babu:**

> "HLD Architecture দেখায়। LLD Details দেখায়।"

**DevOps_Taj:**

> "Terraform + Ansible দিয়ে Infrastructure Provision করি।"

**NetMan_Khalid:**

> "Every Infrastructure Change will follow SDLC."

---

# 💡 The Impact Summary

```text
═══════════════════════════════════════════════════════════════
📊 IMPACT SUMMARY
═══════════════════════════════════════════════════════════════

Before
├── Random Work
├── Requirement Changes
├── Compliance Risk
└── Audit Failure

After
├── Clear Requirement
├── Proper Design
├── Compliance Passed
└── Audit Ready
═══════════════════════════════════════════════════════════════
```

---

# 🗣️ Interview Q&A

## Q1. SDLC কী?

**Answer**

> SDLC হলো Standard Process। Phase: Planning, Define, Design, Build, Test, Deploy।

---

## Q2. Infrastructure DevOps Engineer কোন Phase-এ বেশি কাজ করে?

**Answer**

> Build, Test এবং Deploy Phase-এ।

---

## Q3. HLD এবং LLD-এর পার্থক্য?

**Answer**

> HLD Overall Architecture দেখায়। LLD Detailed Implementation দেখায়।

---

## Q4. Planning/Design Skip করলে কী হয়?

**Answer**

> Requirement miss হয়, Rework হয়, Compliance Risk তৈরি হয়।

---

## Q5. Infrastructure Build মানে কী?

**Answer**

> Terraform এবং Ansible দিয়ে Infrastructure Provisioning করা।

---

# 🎯 Self-Introduction (Updated)

```text
1. হ্যালো, আমি NetMan_Khalid। Infrastructure DevOps Engineer।
2. Terraform এবং Ansible দিয়ে Infrastructure Automation করি।
3. SDLC Follow করি।
4. Build, Test এবং Deploy-এ কাজ করি।
5. Security, Compliance এবং Audit Maintain করি।
```

---

# 📌 5 Key Takeaways

```text
1. SDLC = Planning → Define → Design → Build → Test → Deploy
2. Infrastructure DevOps Zone = Build + Test + Deploy
3. Terraform + Ansible = Infrastructure Build
4. HLD = Architecture, LLD = Details
5. Planning Skip করবেন না।
```

---

# ✅ Completion Checklist

```text
□ SDLC-এর 6টি Phase
□ Build, Test, Deploy
□ HLD vs LLD
□ Centralized Logging Example
□ Infrastructure Build Meaning
```

---

# 📖 গল্পের শেষ

**NetMan_Khalid**

> "SDLC follow করলাম। Project success।"

**Compliance_Rassell**

> "Head Office happy।"

**Audit_Mahfuz**

> "Audit ready।"

**SA_Asraf**

> "Random work আর না।"

```text
🎉 THE END 🎉

Remember:
SDLC is the foundation of Enterprise IT.
```