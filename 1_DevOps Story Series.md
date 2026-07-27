# 🏦 Nord Bank - DevOps Story Series

---

# Episode 01: The Infrastructure Awakening

📖 **তারিখ:** Monday, 15 January, 9:00 AM  
📍 **স্থান:** Nord Bank Headquarters, Dhaka

---

## 🌅 Scene 1: The Morning Crisis

NetMan_Khalid সবেমাত্র Coffee হাতে বসেছেন। NOC_Jahid আর ATM_Shekhor একসঙ্গে দৌড়ে এলেন।

> **ATM_Shekhor:** "NetMan_Khalid ভাই! CEO-র ফোন! 50টা নতুন ATM বসাতে হবে—আগামী সপ্তাহের মধ্যে!"
>
> **NetMan_Khalid:** "50টা মানে 50টা নতুন server! আমাদের তো 10-15 দিন লাগে!"
>
> **NOC_Jahid:** "Competitor bank আমাদের market share নিয়ে নেবে যদি time মেটাতে না পারি!"

---

## 🏢 Scene 2: Emergency Meeting

NetMan_Khalid দ্রুত মিটিং ডাকলেন:

- Infra_Babu (Infrastructure Architect)
- DevOps_Taj (DevOps Engineer)
- SA_Asraf (System Administrator)
- Security_Shahed (Security Specialist)
- Compliance_Rassell (Compliance Lead)
- NOC_Jahid (NOC Lead)

> **NetMan_Khalid:** "7 দিনে 50টা server লাগবে। কী করব?"
>
> **Infra_Babu:** "Manual process-এ System Admin → Build/Release → Server Admin → Production—এতে 10-15 দিন লাগে!"
>
> **DevOps_Taj:** "Infrastructure DevOps দিয়ে ঘন্টায় কাজ শেষ করা যায়। Training-এ দেখেছি।"

---

## 💡 Scene 3: The 4 Pillars (AQMT)

> **NetMan_Khalid:** "DevOps_Taj ঠিক বলেছে। 4টা Pillar—"

```
═══════════════════════════════════════════════════════════════
      INFRASTRUCTURE DEVOPS - 4 PILLARS
═══════════════════════════════════════════════════════════════

🔧 AUTOMATION (A) → Terraform, Ansible
✅ QUALITY (Q)    → Security, PCI-DSS
📊 MONITORING (M) → Prometheus, Grafana
🧪 TESTING (T)    → Staging Environment
```

> **Compliance_Rassell:** "AQMT! কিন্তু compliance?"
>
> **Security_Shahed:** "আর PCI-DSS?"
>
> **NetMan_Khalid:** "Quality pillar-এ সব compliance code-এ থাকবে!"

---

## 🔧 Scene 4: Live Demo

DevOps_Taj ল্যাপটপ খুললেন:

> "ম্যানুয়ালে ৬টা স্টেপ—System Admin, Network, Security, Build, Test, Operations—প্রতিটায় 1-2 days। Total 10 days।"
>
> "Automation দিয়ে—"

```
═══════════════════════════════════════════════════════════════
AUTOMATION TOOLS & THEIR WORK
═══════════════════════════════════════════════════════════════

🔧 TERRAFORM → AWS EC2, VPC, Security Group (50 servers in 1 min)
🔧 ANSIBLE  → Software Install, Network Config (Cisco, Dell, FortiGate)
🔧 BASH     → Testing, Connectivity Check (Smoke Test)
```

> **SA_Asraf:** "50টা server 1 মিনিটে?!"
>
> **DevOps_Taj:** "হ্যাঁ। Terraform এক কমান্ডে সব create করে!"

---

## 🏛️ Scene 5: Nord Bank Infrastructure

NetMan_Khalid Data Center-এ নিয়ে গেলেন:

```
═══════════════════════════════════════════════════════════════
🏦 NORD BANK INFRASTRUCTURE INVENTORY
═══════════════════════════════════════════════════════════════

🌐 Cisco ASR 1000     → NOC_Jahid (Routing)
🖥️ Dell PowerEdge R750 → SA_Asraf (Servers)
🔒 FortiGate 3000F    → Security_Shahed (Firewall)
📊 SolarWinds+Dynatrace → NOC_Jahid (Monitoring)
```

---

## ⚡ Scene 6: Implementation Plan

NetMan_Khalid plan দিলেন:

```
═══════════════════════════════════════════════════════════════
7-DAY IMPLEMENTATION PLAN
═══════════════════════════════════════════════════════════════

Day 1-2: Automation Setup (Terraform + Ansible + GitHub)
Day 3-4: Testing (Staging + Security + Compliance)
Day 5: Monitoring Setup (Grafana + Alerts)
Day 6: Production Deploy (50 servers)
Day 7: Handover + Documentation
```

> **Finance_Arif** (হঠাৎ এসে): "Cost?"
>
> **DevOps_Taj:** "Auto-scaling use করলে 40% cost কমবে!"

---

## 💥 Scene 7: Security & Compliance

> **Security_Shahed:** "PCI-DSS mandatory! আর Audit_Mahfuz-কে তো audit দিতে হবে!"
>
> **NetMan_Khalid:** "সব code-এ integrated—"

```
═══════════════════════════════════════════════════════════════
✅ SECURITY & COMPLIANCE CHECKS (Automated)
═══════════════════════════════════════════════════════════════

1. VPC Private subnet ✅
2. Security Group (only required ports) ✅
3. IAM Least Privilege ✅
4. KMS Encryption ✅
5. CloudTrail Logging ✅
6. PCI-DSS Checklist ✅
```

> **Audit_Mahfuz** (নিজেই চলে এসে): "GitHub-এ সব থাকলে audit easy! I support!"

---

## 🎯 Scene 8: The Big Day (Day 6)

DevOps_Taj command দিলেন:

```
STEP 1: Terraform → 50 server তৈরি (45 seconds)
STEP 2: Ansible → সব server configure (2 minutes)
STEP 3: Security Script → সব check ✅
STEP 4: Test Script → 50/50 server সাড়া দিচ্ছে ✅
```

5 minutes পর—

> **DevOps_Taj:** "NetMan_Khalid ভাই! 50টা server ready!"
>
> **SA_Asraf:** "10 days-এর কাজ 5 minutes-এ!"

---

## 🎉 Scene 9: Celebration

> **NetMan_Khalid:** "Team, 50টা নতুন ATM server ready!"
>
> **ATM_Shekhor:** "10-15 days-এর কথা ছিল!"
>
> **Finance_Arif:** "Cost 40% কম! Budget-এর মধ্যেই!"
>
> **Compliance_Rassell:** "Compliance ✅"
>
> **Security_Shahed:** "Security ✅"
>
> **Audit_Mahfuz:** "GitHub PR, code review, approvals—সব Perfect!"

---

## 📖 Scene 10: The Transformation

```
═══════════════════════════════════════════════════════════════
  OLD MINDSET → NEW MINDSET
═══════════════════════════════════════════════════════════════

OLD: "এটা সম্ভব না"           → NEW: "আমরা automate করে ফেলি"
OLD: "আলাদা টিম approve"     → NEW: "Code review"
OLD: "ডকুমেন্টেশন পরে"       → NEW: "Code is documentation"
OLD: "10 days লাগে"          → NEW: "5 minutes-এ শেষ"
```

---

## 💡 Impact Summary (Episode 01)

```
═══════════════════════════════════════════════════════════════
📊 BEFORE vs AFTER
═══════════════════════════════════════════════════════════════

Server Delivery:  10-15 days → 5 minutes (95% faster)
Team Involvement: 5+ teams → 1 DevOps team
Cost:             High → 40% saving
Compliance:       Risky → Managed
Audit:            Complex → Easy (GitHub)
```

---

## 🗣️ Interview Q&A (Episode 01)

| প্রশ্ন | উত্তর |
|--------|--------|
| **Q1: Infrastructure DevOps কী?** | Code + Automation দিয়ে Infrastructure Manage করা। 10 days → 5 minutes। |
| **Q2: 4 Pillars?** | AQMT: Automation, Quality, Monitoring, Testing। |
| **Q3: Software vs Infrastructure DevOps?** | Software = Application Pipeline (Jenkins)। Infrastructure = Server/Network Pipeline (Terraform)। |

---

## 🎯 Self-Introduction (NetMan_Khalid)

```
═══════════════════════════════════════════════════════════════
MAC Matrix - INFRASTRUCTURE DEVOPS ENGINEER
═══════════════════════════════════════════════════════════════

1. "হ্যালো, আমি MAC Matrix, Infrastructure DevOps Engineer।"

2. "Automation-এ বিশ্বাস করি—manual কাজ কমাতে চাই।"

3. "Linux, Networking, Cloud basics আছে। Terraform/Ansible জানি।"

4. "Nord Bank-এ Delivery automate করব—AQMT follow করব।"

5. "শেখার আগ্রহ বেশি, team-এ কাজ করতে পারি।"
```

---

## 📌 5 Key Takeaways (Episode 01)

1. Infrastructure DevOps = Code + Automation (10 days → 5 min)
2. 4 Pillars = AQMT
3. Tools: Terraform, Ansible, Bash, Prometheus, Grafana
4. Compliance + Security = Built-in
5. Cost Optimization = Auto-scaling (40% saving)

---

## 📋 LAB Scenarios (Episode 01)

```
═══════════════════════════════════════════════════════════════
📋 LAB SCENARIO SUMMARY
═══════════════════════════════════════════════════════════════

***LAB: 01_Infrastructure_DevOps_Concept***
Scenario: Infrastructure DevOps Concept বুঝতে হবে। 4 Pillars
(AQMT) এবং Manual vs Automated Process-এর পার্থক্য বুঝতে হবে।
Nord Bank-এর Context-এ কীভাবে Automation কাজ করে সেটা বুঝতে হবে।

─────────────────────────────────────────────────────────────

***LAB: 02_Nord_Bank_Infrastructure_Inventory***
Scenario: Nord Bank-এর Infrastructure Inventory চিহ্নিত করতে হবে।
Cisco Router, Dell Server, FortiGate Firewall—প্রতিটা Device-এর
কাজ এবং কোন Team Manage করে সেটা বুঝতে হবে।

─────────────────────────────────────────────────────────────

***LAB: 03_Infrastructure_DevOps_Tools_Overview***
Scenario: Infrastructure DevOps-এর Tools—Terraform, Ansible, Bash—
এদের কাজ বুঝতে হবে। কোন Tool কী কাজে ব্যবহার হয় সেটা বুঝতে হবে।

─────────────────────────────────────────────────────────────

***LAB: 04_Security_Compliance_Checklist***
Scenario: Nord Bank-এর Security & Compliance Checklist তৈরি করতে
হবে। VPC, Security Group, IAM, Encryption, Logging, PCI-DSS—সব
Check করতে হবে।
═══════════════════════════════════════════════════════════════
```

> **NetMan_Khalid:** "এটা শুধু শুরু। Docker, Kubernetes—সব।"
>
> **Security_Shahed:** "Security first!"
>
> **Compliance_Rassell:** "Compliance always!"
>
> **Audit_Mahfuz:** "Audit-ready code!"

```
🎉 EPISODE 01 END 🎉
Remember: Infrastructure DevOps is a Culture, not just tools!
```

---

---