# 🏦 Episode 01: The Server Crisis

**📖 Date:** Monday, 15 January, 9:00 AM
**📍 Location:** Nord Bank Headquarters, Dhaka

---

# 👥 Characters

```text
═══════════════════════════════════════════════════════════════
CHARACTERS - EPISODE 01
═══════════════════════════════════════════════════════════════

1. NetMan_Khalid       → Infrastructure DevOps Lead 
2. ATM_Shekhor         → ATM Operations Team Lead
3. NOC_Jahid           → NOC Team Lead
4. Infra_Babu          → Infrastructure Architect 
5. SA_Asraf            → System Administrator 
6. DevOps_Taj          → DevOps Engineer
7. Security_Shahed     → Security Specialist (SOC Team)
8. Compliance_Rassell  → Compliance Lead
9. Finance_Arif        → Finance Team
10. Audit_Mahfuz       → Audit Team Lead
```

---

# 🌅 Scene 1: The Problem

ATM_Shekhor দৌড়ে NetMan_Khalid-এর ডেস্কে এলো।

> **ATM_Shekhor:**
> "Khalid ভাই, বড় সমস্যা। CEO ফোন দিয়েছিলেন। ৭ দিনের মধ্যে ৫০টা নতুন ATM বসাতে হবে।"

> **NetMan_Khalid:**
> "৫০টা ATM মানে ৫০টা Server লাগবে। কিন্তু আমরা তো ১টা Server বসাতেই ১০-১৫ দিন লাগাই।"

> **NOC_Jahid:**
> "Competitor bank আগে চলে যাচ্ছে। CEO বলেছেন, এইবার miss হলে সবার bonus বন্ধ।"

> **NetMan_Khalid:**
> "একা এই কাজ হবে না। পুরো টিমকে নিয়ে বসতে হবে, এখনই।"

---

# 🏢 Scene 2: Emergency Meeting

সবাই Conference Room-এ এসে বসল।

> **NetMan_Khalid:**
> "৭ দিনে ৫০টা Server লাগবে। কার কী মত?"

> **Infra_Babu:**
> "আমাদের Data Center-এ জায়গা প্রায় শেষ। নতুন ৫০টা Server রাখার মতো Space নেই।"

> **SA_Asraf:**
> "আর Manual ভাবে এক-একটা Server বসাতে গেলে তো এমনিতেই ১০-১৫ দিন লাগে। ৭ দিনে সম্ভব না।"

> **DevOps_Taj:**
> "একটা রাস্তা আছে। On-Premise-এর পাশে AWS Cloud ব্যবহার করি। Automation দিয়ে Server বসালে সেটা মিনিটের মধ্যে হয়ে যায়, দিনের মধ্যে না।"

> **NetMan_Khalid:**
> "তাহলে আমরা দুইটাই ব্যবহার করব — কিছু On-Premise-এ, কিছু Cloud-এ। একে বলে Hybrid Infrastructure।"

---

## 💡 Learning Point

সবাই এখনো "Infrastructure Automation" জিনিসটা ঠিক বোঝেনি।

তাই Khalid প্রথমে সহজ করে একটা Framework বোঝাল — **AQMT**।

---

# 💡 Scene 3: AQMT — চার কথায়

```text
🔧 A - Automation   → Terraform, Ansible দিয়ে কাজ automatic হবে
✅ Q - Quality      → Security ও নিয়ম মেনে কাজ
📊 M - Monitoring   → সব সময় নজর রাখা (Grafana, CloudWatch)
🧪 T - Testing      → Live করার আগে Staging-এ টেস্ট
```

> **Security_Shahed:**
> "Banking-এর জন্য Security কোথায় fit করবে এখানে?"

> **NetMan_Khalid:**
> "Quality-র মধ্যেই। Security, Compliance — সব Quality-র অংশ।"

> **Compliance_Rassell:**
> "একটা বড় প্রশ্ন আছে। AWS-এর যে Region ব্যবহার করবেন — সেটা কোন দেশে?"

> **DevOps_Taj:**
> "Mumbai, India। ap-south-1।"

> **Compliance_Rassell:**
> "তাহলে সমস্যা। Bangladesh Bank-এর নিয়ম অনুযায়ী Customer বা Transaction Data দেশের বাইরে রাখা যায় না, আগে অনুমতি ছাড়া। সেটা ৭ দিনে পাওয়া যাবে না।"

> **NetMan_Khalid:**
> (একটু থেমে) "ঠিক আছে। তাহলে ভাগ করে ফেলি। Customer Data, Transaction — সব On-Premise-এই থাকবে, যেমন আছে তেমনই। AWS ব্যবহার করব শুধু Monitoring, Testing আর নতুন ATM-এর Connectivity check-এর কাজে। Sensitive কিছু Cloud-এ যাবে না।"

> **Compliance_Rassell:**
> "এইভাবে হলে আমার আপত্তি নেই।"

---

## 💡 Learning Point

এখানেই আসল শিক্ষা — Cloud মানেই সব কিছু Cloud-এ তুলে দেওয়া না।

কোনটা Cloud-এ যাবে, কোনটা যাবে না — সেটা ঠিক করাই আসল কাজ।

---

# ⚡ Scene 4: টুলগুলো কী করে

```text
🔧 Terraform  → একটা Command দিলে অনেকগুলো Server তৈরি করে দেয়
🔧 Ansible    → Server-এ Software বসায়, Setting ঠিক করে
🔧 Bash       → ছোট ছোট Script দিয়ে Test করা, Connection check করা
```

> **SA_Asraf:**
> "এইগুলো দিয়ে কি সত্যিই এত তাড়াতাড়ি হবে?"

> **DevOps_Taj:**
> "আজকে সবার সামনে Test করে দেখাবো।"

---

# 🏛️ Scene 5: Nord Bank-এর Infrastructure

```text
🏢 ON-PREMISE (আগে থেকেই আছে)
Server: Dell PowerEdge R750, R940
Storage: Dell EMC Unity, IBM TS4500
Network: Cisco ASR1000, Catalyst 9500
Security: FortiGate 3000F, Cisco Firepower
Core Banking: Temenos T24 (এখানেই থাকবে, Cloud-এ যাবে না)

☁️ AWS CLOUD (নতুন, শুধু non-sensitive কাজের জন্য)
Region: ap-south-1 (Mumbai)
Compute: EC2
Storage: EBS, S3
Monitoring: CloudWatch
```

> **Infra_Babu:**
> "তাহলে Core Banking On-Premise-এই থাকছে, শুধু নতুন Monitoring আর Test Environment যাবে Cloud-এ। এতে Space সমস্যাও কমল, নিয়মও ভাঙল না।"

---

# 📋 Scene 6: ৭ দিনের Plan

```text
Day 1  → Automation Tools সেটআপ (Terraform, Ansible)
Day 2  → Script লিখে টেস্ট করা
Day 3  → Staging Environment-এ চালিয়ে দেখা
Day 4  → Security Check
Day 5  → Monitoring বসানো
Day 6  → Production-এ আসল Deployment
Day 7  → Documentation ও হ্যান্ডওভার
```

> **Finance_Arif:**
> "Cloud-এ খরচ কেমন হবে?"

> **DevOps_Taj:**
> "এখন সব Server সব সময় চালু রাখলে খরচ বেশি হবে। কিন্তু দরকার অনুযায়ী Server বাড়ানো-কমানো গেলে (Auto Scaling), হিসাব করে দেখেছি মাসে খরচ প্রায় ৪০% কম আসবে on-premise-এ নতুন সার্ভার কেনার তুলনায়।"

> **Finance_Arif:**
> "সেই হিসাবটা লিখিত আকারে চাই।"

> **DevOps_Taj:**
> "আজকেই পাঠাচ্ছি।"

---

# 🔒 Scene 7: Security Check

```text
🏢 On-Premise: Firewall Rules, VLAN আলাদা, Backup ঠিকঠাক
☁️ AWS: Private Subnet, Security Group, IAM-এ শুধু দরকারি Access, Encryption, CloudTrail Log
```

> **Audit_Mahfuz:**
> "সব কাজ GitHub-এ আর CloudTrail-এ লেখা থাকলে Audit করা সহজ হবে।"

---

# ✅ Scene 8: Day 6 — আসল Deployment

> **DevOps_Taj:**
> "Terraform চালাচ্ছি... ৫০টা Server তৈরি হচ্ছে।"

(কিছুক্ষণ পর)

> **DevOps_Taj:**
> "৪৭টা Server ঠিকমতো উঠেছে। ৩টা Fail করেছে — একটা ভুল Setting-এর জন্য, ঠিক করছি।"

> **SA_Asraf:**
> "তাহলে পুরোটা perfect হয়নি প্রথমবারে?"

> **DevOps_Taj:**
> "না, এটাই স্বাভাবিক। Manual হলে এই ৩টা Server-ও ঠিক করতে আরও ২-৩ দিন লাগত। Script ঠিক করে আবার চালালাম।"

(১৫ মিনিট পর)

> **DevOps_Taj:**
> "৫০টা Server-ই এখন Ready। মোট সময় লেগেছে ঘণ্টাখানেক — Manual হলে যেটা লাগত ১০-১৫ দিন।"

> **Infra_Babu:**
> "Space সমস্যাও নেই, কারণ এগুলো On-Premise-এ বসাইনি।"

> **ATM_Shekhor:**
> "তাহলে ATM Deployment-এর জন্য আমরা রেডি।"

---

## 📊 আগে vs পরে

```text
আগে
• শুধু On-Premise
• ১টা Server-ই ১০-১৫ দিন
• ৫০টা Server ৭ দিনে অসম্ভব

পরে
• Hybrid (On-Premise + Cloud, ঠিক ভাগ করে)
• ৫০টা Server প্রায় ১ ঘণ্টায় (৩টা retry সহ)
• Customer Data দেশের বাইরে যায়নি
```

---

# 🗣️ Interview Questions

**Q1. Infrastructure DevOps কী?**
Code আর Automation দিয়ে Infrastructure দ্রুত ও নির্ভরযোগ্যভাবে তৈরি ও পরিচালনা করা।

**Q2. AQMT কী?**
Automation, Quality, Monitoring, Testing।

**Q3. সব কিছু কি Cloud-এ তুলে দেওয়া উচিত?**
না। কোনটা Sensitive (যেমন Customer Data), কোনটা না — সেটা আগে ঠিক করে তারপর ভাগ করতে হয়। এই গল্পে Core Banking On-Premise-এ রয়ে গেছে, Regulatory কারণে।

---

# 📌 পাঁচটা মূল শিক্ষা

```text
1. Automation মানে কাজ দ্রুত হওয়া, ভুল না হওয়া না — 
   প্রথমবারে ছোটখাটো Fail হতেই পারে, সেটাও Plan-এর অংশ।

2. Cloud ব্যবহারের আগে জানতে হবে — কোন Data কোথায় রাখা যায়, 
   বিশেষ করে Banking-এ Regulatory Rule থাকে।

3. Hybrid মানে সব কিছু ভাগ করে ব্যবহার করা, 
   পুরোটা এক জায়গায় না ফেলা।

4. Terraform, Ansible, Bash — এই তিনটা টুল দিয়েই 
   বেশিরভাগ Automation-এর কাজ শুরু করা যায়।

5. যেকোনো Cost বা Time-এর দাবি (যেমন "৪০% কম") 
   একটা হিসাবের ভিত্তিতে হওয়া উচিত, শুধু কথায় না।
```

---

# 🎉 Episode 01 শেষ

```text
📖 Previous : Introduction
📖 Next     : Episode 02 - Enterprise SDLC
```
