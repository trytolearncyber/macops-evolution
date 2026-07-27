# 🏦 Episode 01: The Server Crisis

**📖 Date:** Monday, 15 January, 9:00 AM  
**📍 Location:** Nord Bank Headquarters, Dhaka

---

# 👥 Characters Introduced

```text
═══════════════════════════════════════════════════════════════
CHARACTERS - EPISODE 01
═══════════════════════════════════════════════════════════════

MAIN CHARACTERS
───────────────────────────────────────────────────────────────

1. NetMan_Khalid
   → Infrastructure DevOps Lead (10+ Years)

2. ATM_Shekhor
   → ATM Operations Team Lead

3. NOC_Jahid
   → NOC Team Lead

4. Infra_Babu
   → Infrastructure Architect (10 Years)

5. SA_Asraf
   → System Administrator (15 Years)

6. DevOps_Taj
   → DevOps Engineer

7. Security_Shahed
   → Security Specialist (SOC Team)

8. Compliance_Rassell
   → Compliance Lead

9. Finance_Arif
   → Finance Team

10. Audit_Mahfuz
    → Audit Team Lead
```

---

# 🌅 Scene 1: The Problem

ATM_Shekhor দ্রুত NetMan_Khalid-এর ডেস্কে এলেন।

> **ATM_Shekhor:**  
> "Khalid ভাই! CEO-র ফোন! আগামী সপ্তাহের মধ্যে ৫০টি নতুন ATM বসাতে হবে!"

> **NetMan_Khalid:**  
> "৫০টি ATM মানে ৫০টি নতুন Server! আমাদের তো Server Provision করতে ১০-১৫ দিন লাগে!"

> **NOC_Jahid:**  
> "Competitor Bank market share নিয়ে যাচ্ছে। CEO বলেছেন, এই Expansion মিস করলে Bonus বন্ধ!"

> **NetMan_Khalid:**  
> "এটা বড় সমস্যা। দ্রুত সমাধান দরকার।"

---

> 💡 **Problem**

একজন মানুষের পক্ষে এই কাজ করা সম্ভব নয়।

পুরো Infrastructure Team-কে একসাথে পরিকল্পনা করতে হবে।

---

# 🏢 Scene 2: Emergency Meeting

Conference Room-এ সবাই উপস্থিত।

**Present**

- Infra_Babu
- SA_Asraf
- Security_Shahed
- NOC_Jahid
- DevOps_Taj
- Compliance_Rassell
- Finance_Arif
- Audit_Mahfuz

---

> **NetMan_Khalid**

"৭ দিনের মধ্যে ৫০টি Server লাগবে। কী করা যায়?"

---

> **Infra_Babu**

"আমাদের On-Premise Data Center ইতিমধ্যে অনেক Server দিয়ে পূর্ণ। নতুন Server যোগ করলে Space শেষ হয়ে যাবে।"

---

> **SA_Asraf**

"Manual Process-এ ১০-১৫ দিন লাগে। ৭ দিনে সম্ভব না।"

---

> **DevOps_Taj**

"On-Premise-এর পাশাপাশি AWS Cloud ব্যবহার করা যায়।

Infrastructure DevOps এবং Automation ব্যবহার করলে ঘণ্টার মধ্যে Infrastructure তৈরি করা সম্ভব।"

---

> **NetMan_Khalid**

"ঠিক বলেছো। আমাদের Hybrid Infrastructure Strategy নিতে হবে।"

---

## 💡 Learning Point

Automation-এ সবাই Infrastructure DevOps সম্পর্কে পরিষ্কার ধারণা রাখে না।

তাই প্রথমে AQMT Framework বোঝানো হবে।

---

# 💡 Scene 3: The Four Pillars (AQMT)

NetMan_Khalid বোর্ডে লিখলেন—

```text
═══════════════════════════════════════════════════════════════
THE FOUR PILLARS (AQMT)
═══════════════════════════════════════════════════════════════

🔧 AUTOMATION (A)
Terraform
Ansible

✅ QUALITY (Q)
Security
PCI-DSS

📊 MONITORING (M)
Prometheus
Grafana

🧪 TESTING (T)
Staging Environment
```

---

> **Security_Shahed**

"Banking Sector-এর Security?"

---

> **NetMan_Khalid**

"Quality Pillar-এর মধ্যেই Security, Compliance এবং Best Practice রয়েছে।"

---

> **Compliance_Rassell**

"Compliance?"

---

> **NetMan_Khalid**

"সব Infrastructure Code-এর মাধ্যমে তৈরি হবে।

Audit যেকোনো সময় করা যাবে।"

---

> **Audit_Mahfuz**

"GitHub-এ Version History থাকলে Audit অনেক সহজ হবে।"

---

# ⚡ Scene 4: Infrastructure Tools

DevOps_Taj Automation Tools দেখালেন।

```text
═══════════════════════════════════════════════════════════════
TOOLS & THEIR WORK
═══════════════════════════════════════════════════════════════

🔧 Terraform
→ 50 Servers in 1 Minute

🔧 Ansible
→ Software Installation
→ Network Configuration

🔧 Bash
→ Testing
→ Connectivity Check
```

---

> **SA_Asraf**

"৫০টি Server এক মিনিটে?"

---

> **DevOps_Taj**

"Terraform একটি Command থেকেই Infrastructure তৈরি করতে পারে।"

---

# 🏛️ Scene 5: Nord Bank Infrastructure

```text
═══════════════════════════════════════════════════════════════
NORD BANK INFRASTRUCTURE
═══════════════════════════════════════════════════════════════

🏢 ON-PREMISE (Existing)

Data Center
• Nord Bank Headquarters

Physical Servers
• Dell PowerEdge R750
• Dell PowerEdge R940

Storage
• Dell EMC Unity
• IBM TS4500

Networking
• Cisco ASR1000
• Cisco Catalyst 9500

Security
• FortiGate 3000F
• Cisco Firepower

Virtualization
• VMware ESXi

Core Banking
• Temenos T24


☁️ AWS CLOUD (New)

Region
• ap-south-1 (Mumbai)

Compute
• Amazon EC2

Storage
• Amazon EBS
• Amazon S3

Networking
• Amazon VPC
• Subnet
• Security Group

Monitoring
• Amazon CloudWatch
```

---

> **NetMan_Khalid**

"Core Banking On-Premise-এ থাকবে।

নতুন Workload AWS Cloud-এ যাবে।"

---

> **Infra_Babu**

"Hybrid Infrastructure আমাদের Space Problem সমাধান করবে।"

---

# 📋 Scene 6: Seven-Day Plan

```text
═══════════════════════════════════════════════════════════════
7-DAY IMPLEMENTATION PLAN
═══════════════════════════════════════════════════════════════

Day 1
Automation Setup

Day 2
Terraform + Ansible

Day 3
Staging Environment

Day 4
Security Testing

Day 5
Monitoring Setup

Day 6
Production Deployment

Day 7
Documentation & Handover
```

---

> **Finance_Arif**

"Cloud Cost কত হবে?"

---

> **DevOps_Taj**

"Auto Scaling ব্যবহার করলে প্রায় ৪০% Cost কমানো সম্ভব।"

---

# 🔒 Scene 7: Security & Compliance

```text
═══════════════════════════════════════════════════════════════
SECURITY CHECKS
═══════════════════════════════════════════════════════════════

🏢 ON-PREMISE

✅ Firewall Rules
✅ VLAN Segmentation
✅ IBM TS4500 Backup

☁️ AWS

✅ Private Subnet
✅ Security Group
✅ IAM Least Privilege
✅ KMS Encryption
✅ CloudTrail Audit Logging
```

---

> **Audit_Mahfuz**

"GitHub এবং CloudTrail থাকলে Audit অনেক সহজ হবে।"

---

# ✅ Scene 8: The Result

**📅 Day 6 — Production Deployment**

---

> **DevOps_Taj**

"৫০টি AWS Server Ready!

মাত্র ৫ মিনিট লেগেছে।"

---

> **SA_Asraf**

"১০ দিনের কাজ ৫ মিনিটে!"

---

> **Infra_Babu**

"On-Premise-এর Space Problem শেষ।

Cloud-এ নতুন ৫০টি Server যুক্ত হয়েছে।"

---

> **ATM_Shekhor**

"ATM Deployment Ready।"

---

> **Finance_Arif**

"Cloud ব্যবহার করে Cost প্রায় ৪০% কমেছে।"

---

## 📊 Before vs After

```text
═══════════════════════════════════════════════════════════════
BEFORE vs AFTER
═══════════════════════════════════════════════════════════════

BEFORE

• Only On-Premise
• 10–15 Days
• 50 Servers Impossible

AFTER

• Hybrid Infrastructure
• On-Premise + AWS Cloud
• 5 Minutes
• 50 Servers Ready ✅
```

---

# 🗣️ Interview Questions

## Q1. Infrastructure DevOps কী?

**Answer**

Infrastructure-কে Code এবং Automation ব্যবহার করে দ্রুত ও নির্ভরযোগ্যভাবে পরিচালনা করার পদ্ধতি।

---

## Q2. AQMT কী?

**Answer**

- Automation
- Quality
- Monitoring
- Testing

---

## Q3. Nord Bank-এর Infrastructure Strategy কী?

**Answer**

Hybrid Infrastructure

- On-Premise → Core Banking
- AWS Cloud → New Workloads

---

# 🎯 Self Introduction (MAC Matrix)

```text
1. Hello, I am MAC Matrix.
2. I am an Infrastructure DevOps Engineer.
3. I believe in Automation.
4. I work with Terraform and Ansible.
5. I manage both On-Premise and AWS Cloud Infrastructure.
6. I follow AQMT principles.
```

---

# 📌 Five Key Takeaways

```text
1. Infrastructure DevOps = Code + Automation

2. Automation reduces deployment time
   from 10 days to about 5 minutes.

3. AQMT is the foundation of Infrastructure DevOps.

4. Terraform, Ansible and Bash are essential tools.

5. Hybrid Infrastructure combines
   On-Premise with AWS Cloud.
```

---

# 🎉 End of Episode 01

```text
──────────────────────────────────────────────────────────────
📖 Previous : Introduction
📖 Next     : Episode 02 - Enterprise SDLC
──────────────────────────────────────────────────────────────
```