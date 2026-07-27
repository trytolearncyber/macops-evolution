# 🏦 Nord Bank - Episode 01: The Infrastructure Awakening

**📖 তারিখ:** Monday, 15 January, 9:00 AM  
**📍 স্থান:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Morning Crisis

NetMan_Khalid সবেমাত্র অফিসে ঢুকেছেন। Coffee হাতে বসেছেন যখন NOC_Jahid দৌড়ে এসে বলল:

> "Khalid ভাই! বড় সমস্যা! ATM_Shekhor বলছে 50টা নতুন ATM বসাতে হবে—আগামী সপ্তাহের মধ্যে! কিন্তু আমাদের current infrastructure এত নতুন server handle করতে পারবে না!"

NetMan_Khalid চোখ কচলালেন।

> "আমাদের তো নতুন server provision করতে 10-15 দিন লাগে। 50টা ATM মানে 50টা নতুন server।"

NOC_Jahid বলল:

> "ঠিক তাই তো! কিন্তু Business Team বলছে—যদি আমরা time মেটাতে না পারি, তাহলে competitor bank আমাদের market share নিয়ে নেবে!"

ঠিক সেই মুহূর্তে ATM_Shekhor নিজেই দৌড়ে এলেন:

> "Khalid ভাই! CEO-র থেকে ফোন এসেছে। তিনি বলেছেন—যদি আমরা এই Expansion মিস করি, তাহলে আমাদের bonus বন্ধ। 50টা ATM মানে 50টা server।"

---

# 🏢 Scene 2: The Meeting Room Drama

NetMan_Khalid সবাইকে meeting room-এ ডাকলেন:

- Infra_Babu (Infrastructure Architect)
- DevOps_Taj (DevOps Engineer)
- Security_Shahed (Security Specialist)
- SA_Asraf (System Administrator)
- NOC_Jahid (NOC Team Lead)
- Compliance_Rassell (Compliance Team Lead)

NetMan_Khalid বললেন:

> "Team, আমাদের 50টা নতুন server দরকার 7 দিনের মধ্যে। Current manual process-এ 10-15 দিন লাগে।"

Infra_Babu বললেন:

> "আমি 10 বছর ধরে এই কাজ করছি। Manual process-এ তো—Request → System Admin → Build/Release → Server Admin → Production। এতে 10-15 দিন লাগে। 7 দিনে সম্ভব না।"

SA_Asraf যোগ করলেন:

> "Babu ভাই ঠিক বলেছেন। গত মাসে 5টা server দিতে 10 দিন লেগেছিল। 50টা server তো অনেক বেশি সময় লাগবে।"

DevOps_Taj বললেন:

> "But Babu ভাই, আমি recently একটা Training দেখেছি—Infrastructure DevOps নামে। ওখানে দেখা গেছে—Request → Infrastructure DevOps Engineer → Automation Tools → Production। সময় লাগে 1 দিন বা ঘন্টায়।"

Infra_Babu বললেন:

> "10 দিনের কাজ 1 দিনে? এটা কীভাবে সম্ভব?"

---

# 💡 Scene 3: The Revelation

NetMan_Khalid বললেন:

> "বাবু ভাই, এটাই Infrastructure DevOps Culture। 4 pillars দিয়ে explain করি।"

DevOps_Taj whiteboard-এ লিখল:

```text
═══════════════════════════════════════════
      INFRASTRUCTURE DEVOPS - 4 PILLARS
═══════════════════════════════════════════

🔧 AUTOMATION (A)
├── Manual কাজ কমিয়ে Code দিয়ে করা
└── Tools: Terraform, Ansible, Bash

✅ QUALITY (Q)
├── Standard আর Compliance মেনে চলা
└── Security Baseline, PCI-DSS

📊 MONITORING (M)
├── Infrastructure-এর Health দেখা
└── Prometheus, Grafana, CloudWatch

🧪 TESTING (T)
├── পরিবর্তন আগে Test করা
└── Staging Environment
═══════════════════════════════════════════
```

Compliance_Rassell বললেন:

> "AQMT - এই 4টা Pillar। কিন্তু এটা কীভাবে 50টা server 7 দিনে দেবে?"

Security_Shahed বললেন:

> "আর banking sector-এ PCI-DSS compliance mandatory।"

NetMan_Khalid বললেন:

> "ঠিক ধরেছেন। Quality pillar-এ সব compliance integrated থাকে।"

---

# 🔧 Scene 4: The Automation Idea

DevOps_Taj ল্যাপটপ খুললেন:

> "দেখুন Babu ভাই, manual process-এ ধাপগুলো—System Admin (2 days) → Network (1 day) → Security (1 day) → Build (2 days) → Test (2 days) → Ops (2 days)। Total 10 days।"

> "Automation Tools দিয়ে কী করি—"

```text
📋 AUTOMATION TOOLS & THEIR WORK

🔧 TERRAFORM
├── কাজ: Cloud Resource Provisioning
├── করে: AWS EC2, VPC, Security Group
└── ফল: 50টা server 1 মিনিটে তৈরি

🔧 ANSIBLE
├── কাজ: Configuration Management
├── করে: Software Install, Network Config
└── ফল: Cisco Router, Dell Server সব automate

🔧 BASH SCRIPT
├── কাজ: Testing & Validation
├── করে: Connectivity Check, Health Check
└── ফল: Smoke test automate
```

SA_Asraf বললেন:

> "এই Tools দিয়ে 50টা server 1 মিনিটে?"

DevOps_Taj বললেন:

> "হ্যাঁ। Terraform এক কমান্ডে সব create করে। Ansible সব configure করে। Bash script সব test করে।"

Infra_Babu বললেন:

> "এটা AWS-র জন্য। কিন্তু আমাদের on-premise Cisco router, Dell server—এগুলো কীভাবে automate করব?"

NetMan_Khalid বললেন:

> "Ansible দিয়ে। Ansible Cisco router configure করতে পারে, Dell server-এ software install করতে পারে, FortiGate firewall rule দিতে পারে—সব automate করা যায়।"

NOC_Jahid বললেন:

> "Cisco router-এর config automate করা যায়?"

NetMan_Khalid:

> "শুধু router না—Dell server, FortiGate firewall—সব automate করা যায়।"

---

# 🏛️ Scene 5: Nord Bank Infrastructure Tour

NetMan_Khalid সবাইকে data center-এ নিয়ে গেলেন:

```text
═══════════════════════════════════════════════════════════════
🏦 NORD BANK INFRASTRUCTURE INVENTORY
═══════════════════════════════════════════════════════════════

Category          Device               Function              Team Lead
─────────────────────────────────────────────────────────────
🌐 Networking     Cisco ASR 1000       Internet/WAN Routing  NOC_Jahid
🖥️ Servers       Dell PowerEdge R750  App Server           SA_Asraf
🔒 Security      FortiGate 3000F      Firewall             Security_Shahed
📊 Monitoring    SolarWinds + Dynatrace Monitoring          NOC_Jahid
```

SA_Asraf বললেন:

> "আমি তো এখনো manual-এ server বানাই। এই automation-এ আমার কাজ কী?"

NetMan_Khalid বললেন:

> "Asraf vai, আপনার কাজ হবে Code লেখা। Manual server বানানোর বদলে Terraform configuration লিখবেন। আপনার expertise ব্যবহার করে automation improve করবেন।"

---

# ⚡ Scene 6: The Implementation Journey

NetMan_Khalid plan দিলেন:

```text
📋 IMPLEMENTATION PLAN (7 days - 50 servers)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DAY 1-2: AUTOMATION SETUP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├── DevOps_Taj: Terraform configuration (AWS resources)
├── SA_Asraf: Ansible playbook (Software + Config)
├── NOC_Jahid: Network automation script
└── GitHub-এ Code Push

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DAY 3-4: TESTING (Staging Environment)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├── 5 server test deploy in Staging
├── Security_Shahed: Security validation
├── Compliance_Rassell: Compliance check
└── NOC_Jahid: Connectivity test

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DAY 5: MONITORING SETUP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├── CloudWatch metrics configuration
├── Grafana dashboard creation
└── Alert system (email + SMS)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DAY 6: PRODUCTION DEPLOY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├── 50 server production-এ deploy
├── SA_Asraf: Manual verification
└── NOC_Jahid: Smoke test

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DAY 7: HANDOVER & DOCUMENTATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├── Operations team-কে handover
├── Compliance_Rassell: Final sign-off
└── Documentation complete
```

Finance_Arif (হঠাৎ এসে):

> "কিন্তু এতে cost কত?"

DevOps_Taj বললেন:

> "Auto-scaling use করব—শুধু প্রয়োজন মতো server চালু থাকবে। Night-এ কম traffic-এ server কমিয়ে দেব। Cost 40% কমবে।"

Finance_Arif বললেন:

> "40% saving। এটা অনেক বড়।"

---

# 💥 Scene 7: The Challenge

Security_Shahed বললেন:

> "Banking sector-এ PCI-DSS compliance mandatory। আর Audit_Mahfuz-কে তো annual audit দিতে হবে।"

Compliance_Rassell বললেন:

> "ঠিক বলেছেন। সব change documented, approved, এবং auditable হতে হবে।"

NetMan_Khalid বললেন:

> "Quality pillar-এর কথা ভুলি নাই।"

```text
✅ SECURITY & COMPLIANCE CHECKS (Automated)

1. VPC: Private subnet (No public exposure) ✅
2. Security Group: Only required ports open ✅
3. IAM Role: Least privilege principle ✅
4. Encryption: KMS enabled ✅
5. Logging: CloudTrail enabled ✅
6. Compliance: PCI-DSS checklist ✅
```

Audit_Mahfuz (নিজেই চলে এসে):

> "Khalid vai, আমি শুনলাম বড় change আসছে। আমার audit team কীভাবে check করবে?"

NetMan_Khalid:

> "Mahfuz vai, code is the documentation। সবকিছু GitHub-এ। প্রতিটা change-এর Pull Request with approvals। Audit team যেকোনো সময় code review করতে পারে।"

Audit_Mahfuz বললেন:

> "GitHub-এ সব থাকলে audit easy। আমি support করি।"

---

# 🎯 Scene 8: The Big Day - Production Deployment

**Day 6: Production Deployment**

সকাল 10:00টা। সবাই ওয়াররুমে:

- NetMan_Khalid (Leading)
- DevOps_Taj (On terminal)
- SA_Asraf (Watching)
- NOC_Jahid (Monitoring)
- Security_Shahed (Security ready)
- Compliance_Rassell (Compliance ready)
- Audit_Mahfuz (Audit trail watching)

NetMan_Khalid:

> "Today is the day। 50টা server production-এ deploy করব।"

DevOps_Taj command দিলেন:

```text
STEP 1: Terraform → 50 server তৈরি (45 seconds)
STEP 2: Ansible → সব server configure (2 minutes)
STEP 3: Security Script → সব check ✅
STEP 4: Test Script → 50/50 server সাড়া দিচ্ছে ✅
```

5 minutes পর—

DevOps_Taj:

> "Khalid ভাই। 50টা server ready।"

SA_Asraf:

> "10 দিনের কাজ 5 minutes-এ।"

NOC_Jahid:

> "Monitoring-এ সব healthy। No alerts।"

---

# 🎉 Scene 9: The Celebration

NetMan_Khalid meeting room-এ সবাইকে ডাকলেন:

- ATM_Shekhor
- Finance_Arif
- Audit_Mahfuz
- Compliance_Rassell

NetMan_Khalid বললেন:

> "Team, 50টা নতুন ATM server ready।"

ATM_Shekhor:

> "10-15 days-এর কথা ছিল।"

Finance_Arif বললেন:

> "Auto-scaling use করায় cost 40% কম। Budget-এর মধ্যেই।"

Compliance_Rassell:

> "Compliance ✅"

Security_Shahed:

> "Security ✅"

Audit_Mahfuz:

> "GitHub PR, code review, approvals—সব আছে। Most auditable deployment।"

---

# 📖 Scene 10: The Lesson Learned

SA_Asraf বললেন:

> "আমি 15 years manual process-এ কাজ করেছি।"

```text
═══════════════════════════════════════════════════════════════
  OLD MINDSET → NEW MINDSET
═══════════════════════════════════════════════════════════════

OLD: "এটা সম্ভব না"           → NEW: "আমরা automate করে ফেলি"
OLD: "আলাদা টিম approve"     → NEW: "Code review"
OLD: "ডকুমেন্টেশন পরে"       → NEW: "Code is documentation"
OLD: "মানুষের উপর depend"    → NEW: "Automation on depend"
OLD: "10 days লাগে"          → NEW: "5 minutes-এ শেষ"
═══════════════════════════════════════════════════════════════
```

Infra_Babu বললেন:

> "আমি শিখতে চাই এই Automation।"

NetMan_Khalid বললেন:

> "From today—CODE FIRST, AUTOMATE, TEST FIRST, MONITOR, COMPLIANCE, AUDIT—সব।"

---

# 💡 The Impact Summary

```text
═══════════════════════════════════════════════════════════════
📊 BEFORE vs AFTER - INFRASTRUCTURE DEVOPS IMPACT
═══════════════════════════════════════════════════════════════

Server Delivery:  10-15 days → 5 minutes (95% faster)
Team Involvement: 5+ teams → 1 DevOps team
Error Rate:       High → Low (code)
Cost:             High → 40% saving
Compliance:       Risky → Managed
Audit:            Complex → Easy (GitHub)
═══════════════════════════════════════════════════════════════
```

---

# 🗣️ Interview Q&A from this Story

### Q1: "Infrastructure DevOps কী?"

**Answer:**  
"Code + Automation দিয়ে Infrastructure Manage করা। Nord Bank-এ 10 days-এর কাজ 5 minutes-এ করা সম্ভব।"

---

### Q2: "4 Pillars কী?"

**Answer:**  
"AQMT—Automation, Quality, Monitoring, Testing।"

---

### Q3: "কী কী Tools ব্যবহার করেন?"

**Answer:**  
"Terraform (Resource Provisioning), Ansible (Configuration Management), Bash (Testing), Prometheus/Grafana (Monitoring)।"

---

### Q4: "Compliance এবং Audit কীভাবে handle করবেন?"

**Answer:**  
"সব code-এ integrated। GitHub PR, approvals, audit trail।"

---

# 🎯 Self-Introduction Script

```text
1. "হ্যালো, আমি NetMan_Khalid। System Admin থেকে DevOps-এ আসছি।"
2. "Automation-এ বিশ্বাস করি—manual কাজ কমাতে চাই।"
3. "Linux, Networking, Cloud basics আছে। Terraform/Ansible শিখছি।"
4. "Nord Bank-এ Delivery automate করব—AQMT follow করব।"
5. "শেখার আগ্রহ বেশি, team-এ কাজ করতে পারি।"
```

---

# 📌 Key Takeaways

```text
1. Infrastructure DevOps = Code + Automation (10 days → 5 min)
2. 4 Pillars = AQMT
3. Tools: Terraform, Ansible, Bash, Prometheus, Grafana
4. Compliance + Security = Built-in
5. Cost Optimization = Auto-scaling (40% saving)
```

---

# ✅ Completion Checklist

```text
□ Definition বুঝেছি? (Code + Automation)
□ 4 Pillars? (AQMT)
□ Old vs New? (10 days → 5 min)
□ Tools চিনতে পারছি? (Terraform, Ansible, Bash, Prometheus)
□ Devices? (Cisco, Dell, FortiGate, SolarWinds)
□ Self-Intro তৈরি?
□ Interview Questions?
```

---

# 📖 গল্পের শেষ

NetMan_Khalid:

> "এটা শুধু শুরু। Docker, Kubernetes—সব।"

Security_Shahed:

> "Security first।"

Compliance_Rassell:

> "Compliance always।"

Audit_Mahfuz:

> "Audit-ready code।"

```text
🎉 THE END 🎉

Remember: Infrastructure DevOps is a Culture, not just tools।
```