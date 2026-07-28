# 🏦 Nord Bank - Episode 04: AWS EC2

**📖 তারিখ:** Thursday, 18 January, 10:00 AM
**📍 স্থান:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Problem

Infra_Babu NetMan_Khalid-এর ডেস্কে এলেন।

> **Infra_Babu:**
> "Khalid ভাই, On-premise Data Center-এ আর জায়গা নেই। নতুন Server রাখার মতো Room নেই।"

> **NetMan_Khalid:**
> "কিন্তু আমাদের তো আরও Server দরকার।"

> **Infra_Babu:**
> "হ্যাঁ, কিন্তু Data Center Full।"

> **NetMan_Khalid:**
> "তাহলে Cloud-এ যেতে হবে।"

> **Infra_Babu:**
> "Cloud? মানে?"

> **NetMan_Khalid:**
> "AWS। সেখানে Server ভাড়া নেওয়া যায়, কেনার দরকার নেই।"

---

# 🏢 Scene 2: The Meeting

> **NetMan_Khalid:**
> "Team, On-premise Data Center Full। Cloud-এ যেতে হবে।"

> **Finance_Arif:**
> "Multi-Cloud কেন না — AWS, Azure, GCP একসাথে?"

> **DevOps_Taj:**
> "Arif ভাই, Multi-Cloud জটিল। শুরুতে Single-Cloud (AWS) দিয়ে করাই ভালো।"

```text
═══════════════════════════════════════════════════════════════
SINGLE-CLOUD vs MULTI-CLOUD
═══════════════════════════════════════════════════════════════

SINGLE-CLOUD (AWS)              MULTI-CLOUD
├── একটাই Platform শিখলে হয়      ├── প্রতিটা Cloud-এর আলাদা Skill লাগে
├── Cost হিসাব রাখা সহজ           ├── কোন Cloud-এ কত খরচ, ট্র্যাক করা কঠিন
├── একটা Tool-চেইনেই Automation  ├── প্রতিটা Cloud-এর জন্য আলাদা Setup
└── একটাই Compliance Process     └── প্রতিটা Cloud আলাদা Audit করতে হয়

Nord Bank-এর মতো ছোট Team-এর জন্য Single-Cloud দিয়ে শুরু করাটাই
বাস্তবসম্মত। বড় Enterprise-এ Vendor Lock-in এড়াতে Multi-Cloud
বেছে নেয়, কিন্তু সেটার জন্য বেশি Team ও বাজেট লাগে।

Nord Bank Decision: ✅ SINGLE-CLOUD (AWS)
```

> **SA_Asraf:**
> "AWS-এ Server কীভাবে কাজ করে?"

> **NetMan_Khalid:**
> "AWS EC2 — এটাও একটা Virtual Machine। Day 03-এ যা Virtualization নিয়ে শিখেছিলাম, তারই বাস্তব রূপ।"

---

# 💡 Scene 3: EC2 কী?

> **DevOps_Taj:**
> "EC2 মানে Elastic Compute Cloud। Request করলে AWS একটা VM (Instance) বানিয়ে দেয়।"

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
  EC2  EC2  EC2  (Virtual Machines)
```

> **SA_Asraf:**
> "মানে On-premise-এ যেভাবে VMware ব্যবহার করি, ঠিক সেই ধারণা?"

> **NetMan_Khalid:**
> "একদম। Concept একই — Virtualization। শুধু Platform আলাদা।"

---

# 🛠️ Scene 4: EC2 বানানোর পদ্ধতি

> **Infra_Babu:**
> "EC2 Instance কীভাবে তৈরি করব?"

> **DevOps_Taj:**
> "মূলত তিনটা পদ্ধতি এখন শিখলেই যথেষ্ট —"

```text
═══════════════════════════════════════════════════════════════
EC2 CREATION METHODS
═══════════════════════════════════════════════════════════════

✅ Console (UI)  → শেখার সময়, দ্রুত দেখার জন্য
✅ AWS CLI       → Script দিয়ে করার জন্য
✅ Terraform ⭐   → বড় আকারে, বারবার একইভাবে বানানোর জন্য (Best)
```

> **Infra_Babu:**
> "Terraform-কে Best বলছো কেন?"

> **DevOps_Taj:**
> "কারণ একই Code দিয়ে বারবার একইভাবে Infrastructure বানানো যায়, ভুল কম হয়, আর AWS ছাড়া অন্য Cloud-এও একই Tool ব্যবহার করা যায়।"

---

# 🖥️ Scene 5: প্রথম EC2 Instance (Console দিয়ে)

> **SA_Asraf:**
> "Console দিয়ে কীভাবে Instance বানাবো?"

> **DevOps_Taj:**
> "Console-এ গিয়ে Launch Instance-এ Click করতে হবে।"

**ধাপগুলো:**

- Name: `nordbank-test-server`
- OS: Ubuntu 22.04 LTS
- Instance Type: `t2.micro` (Free Tier)
- Key Pair: `nordbank-test-key`
- Launch Instance

DevOps_Taj সবার সামনে Live Demo দেখালেন। প্রায় **5 মিনিটে** Instance Ready হয়ে গেল।

> **SA_Asraf:**
> "মাত্র 5 মিনিটে Server রেডি! On-premise-এ এই কাজ করতে 10-15 দিন লাগত।"

> **NetMan_Khalid:**
> "এটাই Cloud-এর আসল সুবিধা।"

---

# 🔑 Scene 6: Key Pair

> **Security_Shahed:**
> "Key Pair জিনিসটা কী?"

> **NetMan_Khalid:**
> "SSH দিয়ে Login করার Credential।"

```text
═══════════════════════════════════════════════════════════════
KEY PAIR
═══════════════════════════════════════════════════════════════

Public Key   → AWS-এর কাছে থাকে
Private Key  → .pem ফাইল, আপনার কাছে থাকে

⚠️ গুরুত্বপূর্ণ:
├── .pem ফাইল কখনো Git-এ Push করা যাবে না
├── আলাদা Secure Folder-এ রাখতে হবে
└── হারালে সেই Instance-এ আর Login করা যাবে না
```

> **Security_Shahed:**
> "Banking-এ Key Management অনেক গুরুত্বপূর্ণ বিষয়।"

> **NetMan_Khalid:**
> ".pem ফাইল যেন কারো হাতে না যায়, সেটা নিশ্চিত করতে হবে।"

---

# 📋 Scene 7: Free Tier

> **Finance_Arif:**
> "এই Instance-এর খরচ কত?"

> **DevOps_Taj:**
> "এই নির্দিষ্ট Type-টা Free Tier-এর মধ্যে পড়ে।"

```text
═══════════════════════════════════════════════════════════════
AWS FREE TIER
═══════════════════════════════════════════════════════════════

Instance : t2.micro
CPU      : 1 vCPU
RAM      : 1GB
Storage  : 30GB EBS

🆓 নতুন AWS Account-এর জন্য প্রথম 12 মাস ফ্রি (একটা নির্দিষ্ট Limit পর্যন্ত)

উপযুক্ত: শেখা, Testing, ছোট Development কাজ
```

> **Finance_Arif:**
> "Production-এও কি একই Instance ব্যবহার হবে?"

> **NetMan_Khalid:**
> "না। Production-এ `m5.large` বা তার চেয়ে বড় Instance লাগবে, এবং সেটা Free না — সেই খরচ আলাদাভাবে হিসাব করতে হবে।"

---

# ⚡ Scene 8: Public IP ও Connectivity

> **NOC_Jahid:**
> "Instance তৈরি হলে সেটাতে কীভাবে ঢুকব?"

> **DevOps_Taj:**
> "Public IP দিয়ে SSH করা যাবে।"

> **NOC_Jahid:**
> "Public IP দিয়ে সরাসরি Access — এটা কি Security-র দিক থেকে ঝুঁকিপূর্ণ না?"

> **NetMan_Khalid:**
> "ভালো প্রশ্ন। এটা Security Group দিয়ে নিয়ন্ত্রণ করা হয় — কে, কোথা থেকে, কোন Port দিয়ে ঢুকতে পারবে। এই বিষয়টা বিস্তারিতভাবে আমরা পরে, Security নিয়ে আলাদা Episode-এ (Day 12) দেখব।"

---

# ✅ Scene 9: ফলাফল

```text
═══════════════════════════════════════════════════════════════
ON-PREMISE vs AWS EC2
═══════════════════════════════════════════════════════════════

ON-PREMISE                    AWS EC2
├── 10-15 দিন লাগে             ├── প্রায় 5 মিনিট লাগে
├── নিজে Hardware কেনা লাগে     ├── Hardware কেনার দরকার নেই
├── Manual Configuration       ├── অনেকটা Automated
└── আগে থেকেই বড় খরচ (Upfront) └── ব্যবহার অনুযায়ী খরচ (Pay-per-use)
```

> **SA_Asraf:**
> "5 মিনিটে Server — এখনো বিশ্বাস হচ্ছে না!"

> **Finance_Arif:**
> "Pay-per-use মডেলে খরচ কম হবে, তবে ঠিক কতটা কমবে সেটা Production Instance Size আর ব্যবহারের ধরন অনুযায়ী হিসাব করে বলা যাবে — এখনই একটা Fix সংখ্যা বলা ঠিক হবে না।"

---

# 🗣️ Interview Q&A

**Q1. AWS EC2 কী?**
Virtual Machine Service। Day 03-এ শেখা Virtualization-এর বাস্তব রূপ।

**Q2. EC2 বানানোর পদ্ধতি কী কী?**
Console, CLI, Terraform — শুরুতে এই তিনটা জানলেই যথেষ্ট।

**Q3. Nord Bank Single-Cloud কেন বেছে নিল?**
ছোট Team-এর জন্য Skill, Cost ট্র্যাকিং, আর Compliance সহজ রাখতে। বড় Enterপ্রাইজ Vendor Lock-in এড়াতে Multi-Cloud নেয়, কিন্তু তাতে বেশি Team ও বাজেট লাগে।

**Q4. Key Pair কী?**
SSH Login Credential। Private Key (.pem ফাইল) সবসময় Secure রাখতে হয়, Git-এ কখনো Push করা যাবে না।

**Q5. Production-এ কি Console দিয়ে EC2 বানানো হবে?**
না। Terraform বা CLI ব্যবহার করা হবে, যাতে কাজ পুনরাবৃত্তিযোগ্য (Repeatable) হয়।

---

# 🎯 Self Introduction (MAC Matrix)

```text
1. হ্যালো, আমি MAC Matrix, Infrastructure DevOps Engineer।
2. On-premise থেকে AWS Cloud-এ কাজ করছি (Hybrid — On-premise + Cloud)।
3. EC2 Instance তৈরি করি — Console, CLI, Terraform দিয়ে।
4. Nord Bank-এর Single-Cloud (AWS) Strategy অনুসরণ করি।
5. Key Pair, Security Group — সব Secure রাখার দায়িত্বও বুঝি।
```

---

# 📌 5 Takeaways

```text
1. EC2 = Virtual Machine, AWS-এর নিজস্ব Hypervisor-এ চলে।

2. Free Tier (t2.micro) শেখা আর Testing-এর জন্য, Production-এর
   জন্য না।

3. Key Pair-এর Private Key (.pem) হারালে সেই Instance-এ আর
   Login করা যাবে না — তাই Secure রাখা জরুরি।

4. EC2 বানানোর পদ্ধতি: Console, CLI, Terraform — শুরুতে এই তিনটা।

5. Pay-per-use মডেল খরচ কমাতে সাহায্য করে, কিন্তু ঠিক কত কমবে
   সেটা Instance Size আর ব্যবহারের ধরনের ওপর নির্ভর করে —
   আগে থেকে একটা সংখ্যা ধরে না নিয়ে হিসাব করে দেখাই ভালো।
```

---

# 🖥️ Hands-On Labs - Day 04

```text
═══════════════════════════════════════════════════════════════
HANDS-ON LABS - DAY 04
═══════════════════════════════════════════════════════════════

LAB 01: Free_Tier_EC2_Creation
কাজ    → Nord Bank Testing Team-এর জন্য একটা Free Tier EC2
          Instance (t2.micro) তৈরি করা
Output → EC2 Instance তৈরি হয়ে চলছে

LAB 02: Key_Pair_Management
কাজ    → EC2 Instance-এর জন্য একটা Key Pair তৈরি করা, এবং
          .pem ফাইল Secure একটা জায়গায় রাখা
Output → Key Pair তৈরি + SSH দিয়ে সফলভাবে Login
```

---

# 🎉 THE END 🎉

```text
📌 PREVIOUS: 03_Episode_Virtualization_Fundamentals
📌 NEXT: 05_Episode_AWS_CLI_IAM
```
