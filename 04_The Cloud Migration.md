# 🏦 Nord Bank - Episode 04: The Cloud Migration

**📖 তারিখ:** Thursday, 18 January, 10:00 AM  
**📍 স্থান:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Cloud Decision

NetMan_Khalid meeting room-এ সবাইকে ডাকলেন। Agenda: **Cloud Strategy**।

**NetMan_Khalid:**  
> "Team। Management Decision—আমরা Cloud-এ যাচ্ছি। AWS বেছে নেওয়া হয়েছে।"

**Infra_Babu:**  
> "Cloud? মানে আমাদের on-premise data center বন্ধ?"

**NetMan_Khalid:**  
> "হ্যাঁ। ধীরে ধীরে on-premise workload AWS-তে migrate করব।"

**Finance_Arif:**  
> "কিন্তু Multi-Cloud কেন না? AWS + Azure + GCP?"

**DevOps_Taj:**  
> "Arif vai। Multi-Cloud জটিল। Nord Bank-এর জন্য Single-Cloud (AWS) ভালো।"

```text
═══════════════════════════════════════════════════════════════
SINGLE-CLOUD vs MULTI-CLOUD
═══════════════════════════════════════════════════════════════

                    SINGLE-CLOUD (AWS)        MULTI-CLOUD
─────────────────────────────────────────────────────────────
Team Skill         গভীর দক্ষতা তৈরি সহজ     প্রতিটা platform-এ skill লাগে
Cost Management    এক billing model          একাধিক billing model
Automation         এক tool-set               আলাদা tool-set
Compliance         এক framework              একাধিক framework
─────────────────────────────────────────────────────────────

Nord Bank Decision: ✅ SINGLE-CLOUD (AWS)
```

**Finance_Arif:**  
> "AWS-তে server কীভাবে কাজ করে?"

**NetMan_Khalid:**  
> "AWS EC2। এটা Virtual Machine। Day 03-এ আমরা virtualization শিখেছি—এটার বাস্তব রূপ।"

---

# 💡 Scene 2: EC2 Explained

**DevOps_Taj:**  
> "EC2 = Elastic Compute Cloud। Request করলে AWS VM (Instance) তৈরি করে দেয়।"

```text
═══════════════════════════════════════════════════════════════
AWS EC2 = VIRTUAL MACHINE
═══════════════════════════════════════════════════════════════

AWS Data Center
        │
        ▼
Physical Server
        │
        ▼
Nitro Hypervisor (KVM-based)
        │
    ┌───┼───┐
    ▼   ▼   ▼
  EC2  EC2  EC2 (Virtual Machines)
```

**SA_Asraf:**  
> "আমরা কি on-premise VMware-র মতো work করব?"

**NetMan_Khalid:**  
> "Concept same—virtualization। Just different platform।"

---

# 🏗️ Scene 3: EC2 Creation Methods

**Infra_Babu:**  
> "EC2 Instance কীভাবে তৈরি করব?"

**DevOps_Taj:**  
> "6টা method আছে—"

```text
═══════════════════════════════════════════════════════════════
6 EC2 CREATION METHODS
═══════════════════════════════════════════════════════════════

METHOD                   USE CASE
─────────────────────────────────────────────────────────────
1. Console (UI)          শেখার সময় / এক-time কাজ
2. AWS CLI               Scripting / ছোট automation
3. AWS SDK (boto3)       Custom application
4. CloudFormation        AWS-only Infrastructure as Code
5. AWS CDK               Code দিয়ে CFT generate
6. Terraform             Multi-cloud Infrastructure as Code

Nord Bank Choice: ✅ TERRAFORM
```

**Infra_Babu:**  
> "Terraform কেন?"

**DevOps_Taj:**  
> "Industry standard। Multi-cloud support। Large community।"

**NetMan_Khalid:**  
> "আজকে Console দিয়ে শিখব। Production-এ Terraform use করব।"

---

# 🖥️ Scene 4: First EC2 Instance (Console)

**SA_Asraf:**  
> "Console দিয়ে কীভাবে Instance তৈরি করি?"

**DevOps_Taj:**  
> "Console-এ গিয়ে Launch Instance click করতে হবে। Name দিতে হবে, OS Select করতে হবে, Instance Type Select করতে হবে, Key Pair তৈরি করতে হবে, আর Launch করতে হবে।"

DevOps_Taj live demo দেখালেন। 5 minutes-এ Instance ready।

**SA_Asraf:**  
> "এটা তো 10 minutes-এ ready! On-premise-এ 10 days লাগত!"

**NetMan_Khalid:**  
> "এটাই Cloud-এর power।"

---

# 🔑 Scene 5: Key Pair Explained

**Security_Shahed:**  
> "Key Pair কী?"

**NetMan_Khalid:**  
> "SSH Login Credential। Public Key AWS-তে থাকে, Private Key আমাদের কাছে থাকে।"

```text
═══════════════════════════════════════════════════════════════
KEY PAIR
═══════════════════════════════════════════════════════════════

Key Pair = SSH Login Credential

Public Key → AWS-তে থাকে
Private Key → .pem ফাইল (আপনার কাছে থাকে)

⚠️ IMPORTANT:
├── .pem ফাইল কখনো Git-এ Push করবেন না
├── Secure folder-এ রাখুন
└── হারালে Instance-এ Login করা যায় না
```

**Security_Shahed:**  
> "Banking sector-এ key management খুব important। PCI-DSS requirement।"

**NetMan_Khalid:**  
> "ঠিক। .pem file secure রাখতে হবে।"

**Security_Shahed:**  
> "আমাদের Testing Team-এর জন্য কি আলাদা Instance দরকার?"

**NetMan_Khalid:**  
> "হ্যাঁ। Testing Team নতুন feature test করবে। Production-এ direct test করা যায় না।"

> **LAB:** `EC2_Instance_Creation`

---

# 📋 Scene 6: Free Tier Details

**Finance_Arif:**  
> "এই Instance-এর cost কত?"

**DevOps_Taj:**  
> "Free Tier। t2.micro instance—1 vCPU, 1GB RAM—free।"

```text
═══════════════════════════════════════════════════════════════
AWS FREE TIER
═══════════════════════════════════════════════════════════════

INSTANCE: t2.micro
CPU: 1 vCPU
RAM: 1GB
Storage: 30GB EBS

🆓 FREE FOR 12 MONTHS

Best for: Learning, Testing, Development
```

**Finance_Arif:**  
> "Production-এ same instance use করব?"

**NetMan_Khalid:**  
> "না। Production-এ m5.large বা larger instance use করব। Free tier শুধু learning-এর জন্য।"

**Finance_Arif:**  
> "Testing Team-এর Instance কি free tier-এ চলবে?"

**NetMan_Khalid:**  
> "হ্যাঁ। Testing-এর জন্য t2.micro enough। কিন্তু production-এর জন্য larger instance needed।"

> **LAB:** `AWS_Free_Tier_Optimization`

---

# ⚡ Scene 7: Public IP & Connectivity

**NOC_Jahid:**  
> "Instance তৈরি হলে কীভাবে access করব?"

**DevOps_Taj:**  
> "Public IP দিয়ে SSH করব। Key Pair (.pem file) use করে connect করতে হবে।"

**NOC_Jahid:**  
> "Public IP দিয়ে direct access? Security risk না?"

**NetMan_Khalid:**  
> "Security Group manage করে। Day 12-এ বিস্তারিত শিখব।"

**NOC_Jahid:**  
> "Testing Team-কে কি Public IP দিতে হবে? নাকি private IP দিয়ে access করবে?"

**NetMan_Khalid:**  
> "Testing Team VPN দিয়ে access করবে। Public IP শুধু temporary access-এর জন্য।"

> **LAB:** `EC2_SSH_Access_Setup`

---

# 📖 Scene 8: The Lesson

**SA_Asraf:**  
> "আমি 15 years on-premise server-এ কাজ করেছি। Cloud EC2 দেখছি—5 minutes-এ server ready!"

```text
═══════════════════════════════════════════════════════════════
KEY LEARNINGS
═══════════════════════════════════════════════════════════════

ON-PREMISE vs CLOUD (EC2)
─────────────────────────────────────────────────────────────
ON-PREMISE:
├── Server provision: 10-15 days
├── Physical hardware needed
├── Manual configuration
└── High cost

CLOUD (EC2):
├── Server provision: 5 minutes
├── No hardware needed
├── Automated configuration
└── Pay-per-use (lower cost)

EC2 CREATION METHODS:
├── Console (Learning)
├── CLI/SDK (Scripting)
└── Terraform (Production - Nord Bank Choice)

BEST PRACTICES:
├── Production-এ Automation use করুন
├── Key Pair (.pem) secure রাখুন
└── Free Tier দিয়ে শিখুন
```

**Infra_Babu:**  
> "আমি cloud শিখছি। আগে ভয় পেতাম—এখন বুঝি।"

---

# 💡 The Impact Summary

```text
═══════════════════════════════════════════════════════════════
📊 ON-PREMISE vs AWS EC2
═══════════════════════════════════════════════════════════════

                  ON-PREMISE           AWS EC2
─────────────────────────────────────────────────────────────
Provision Time    10-15 days          5 minutes
Hardware Cost     High (CAPEX)        Low (OPEX)
Maintenance       Manual              Managed by AWS
Scalability       Limited             Elastic (Auto-scaling)
```

### Nord Bank Benefit

- 95% faster server delivery
- Lower cost (pay-per-use)
- Focus on business, not hardware

---

# 🗣️ Interview Q&A

### Q1: AWS EC2 কী?

**Answer:**  
"AWS EC2 হলো Virtual Machine Service। AWS Data Center-এর Physical Server-এ Hypervisor (Nitro) দিয়ে VM তৈরি করে দেয়। Day 03-এর Virtualization Theory-র বাস্তব রূপ।"

### Q2: EC2 Instance তৈরির কয়টি উপায় আছে?

**Answer:**  
"6টা—Console (Learning), AWS CLI (Scripting), AWS SDK (Custom App), CloudFormation (AWS-only IAC), AWS CDK (Code to CFT), Terraform (Multi-cloud IAC)। Nord Bank Terraform use করবে।"

### Q3: Nord Bank কেন Single-Cloud (AWS) Strategy বেছে নেবে?

**Answer:**  
"Single-Cloud-এ Team Skill দ্রুত তৈরি হয়, Cost Management সহজ, Automation এক Tool-set-এ করা যায়, Compliance Framework একটাই Follow করতে হয়। Multi-Cloud জটিল।"

### Q4: Key Pair কী? কেন secure রাখতে হবে?

**Answer:**  
"Key Pair হলো SSH Login Credential। .pem ফাইল Private Key—এটা হারালে বা অন্য কেউ পেলে Unauthorized Access পেতে পারে। Banking sector-এ এটা Security Breach।"

### Q5: Production-এ Console দিয়ে EC2 তৈরি করা উচিত নয় কেন?

**Answer:**  
"Manual Creation Error-prone, Repeatable নয়, Version Control-এ রাখা যায় না, Audit-এ Problem হয়। Production-এ Automation (Terraform/CLI) ব্যবহার করতে হয়।"

---

# 🎯 Self-Introduction (Updated)

```text
1. "হ্যালো, আমি NetMan_Khalid। Infrastructure DevOps Engineer।"
2. "On-premise থেকে AWS Cloud-এ কাজ করছি।"
3. "EC2 Instance তৈরি করি—Console, CLI, Terraform দিয়ে।"
4. "Single-Cloud (AWS) Strategy follow করি।"
5. "Key Pair, Security Group—সব secure রাখি।"
```

---

# 📌 5 Key Takeaways

```text
1. EC2 = Virtual Machine (Day 03-এর Virtualization Theory-র বাস্তব রূপ)
2. Free Tier = t2.micro (1 vCPU, 1GB RAM)
3. Key Pair = Login Credential (.pem file secure রাখুন)
4. Creation Methods = 6 (Console → Terraform)
5. Single-Cloud (AWS) = Nord Bank Strategy
```

---

# ✅ Completion Checklist

```text
□ EC2 কী?
□ Single-Cloud vs Multi-Cloud?
□ 6 Creation Methods?
□ Console দিয়ে EC2 তৈরি করতে পারি?
□ Key Pair কী?
□ Production-এ Automation কেন?
```

---

# 🧪 LAB Scenarios from this Episode

```text
═══════════════════════════════════════════════════════════════
📋 LAB SCENARIO SUMMARY
═══════════════════════════════════════════════════════════════

***LAB: EC2_Instance_Creation***
Scenario: Nord Bank Testing Team-এর জন্য Test Environment দরকার।
তারা নতুন Application Feature Test করতে চায়। Production-এ Direct
Test করা যায় না। তাই আলাদা Test EC2 Instance দরকার।

Requirements:
├── Instance Name: nordbank-test-server
├── Operating System: Ubuntu 22.04 LTS
├── Instance Type: t2.micro (Free Tier)
├── Key Pair: nordbank-test-key
└── Purpose: Application Testing

─────────────────────────────────────────────────────────────

***LAB: AWS_Free_Tier_Optimization***
Scenario: Finance_Arif জানতে চায় Testing Environment-এর cost কত।
DevOps_Taj বলে Free Tier use করলে cost zero। কিন্তু Production-এর
জন্য larger instance needed।

Requirements:
├── Identify Free Tier eligible resources
├── Calculate cost for Production instance
└── Document cost optimization strategy

─────────────────────────────────────────────────────────────

***LAB: EC2_SSH_Access_Setup***
Scenario: NOC_Jahid জানতে চায় Testing Team কীভাবে Instance access করবে।
DevOps_Taj বলে Public IP দিয়ে SSH করবে। কিন্তু Security_Shahed
চায় secure access।

Requirements:
├── SSH connection from local machine
├── Key Pair (.pem) usage
├── Security Group configuration
└── VPN access for production
═══════════════════════════════════════════════════════════════
```

---

# 📖 গল্পের শেষ

**NetMan_Khalid:**  
> "AWS EC2 শিখলাম। 5 minutes-এ server ready।"

**SA_Asraf:**  
> "10 days vs 5 minutes—বিশ্বাস হচ্ছে না!"

**Finance_Arif:**  
> "Cost-effective। CEO happy হবে।"

**Security_Shahed:**  
> "Key Pair secure রাখতে হবে।"

**DevOps_Taj:**  
> "Next—CLI and IAM শিখব।"

```text
🎉 THE END 🎉

Remember: EC2 is the foundation of AWS Cloud Computing.
```