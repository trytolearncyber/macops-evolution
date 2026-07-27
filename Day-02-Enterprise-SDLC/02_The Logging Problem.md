# 🏦 Nord Bank - Episode 02: The Logging Problem (Revised)

**📖 Date:** Tuesday, 16 January, 10:00 AM
**📍 Location:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Problem

**Compliance_Rassell** দ্রুত **NetMan_Khalid**-এর ডেস্কে এলেন।

> **Compliance_Rassell:**
> "Khalid ভাই! Head Office থেকে নতুন Regulation এসেছে। Transaction Log এখন থেকে 90 দিন রাখতে হবে।"

> **NetMan_Khalid:**
> "90 দিন? আগে তো 30 দিন ছিল।"

> **Compliance_Rassell:**
> "হ্যাঁ। প্রতিদিন প্রায় 50GB Log হয়। 90 দিন মানে হিসাব করলে 4.5TB Storage লাগবে।"

> **NetMan_Khalid:**
> "এটা ছোট কাজ না। ঠিকমতো Process মেনে করতে হবে, ঝোঁকের বশে না।"

---

# 🏢 Scene 2: The Meeting

> **NetMan_Khalid:**
> "টিম, শোনো। Log 90 দিন রাখতে হবে। রোজ 50GB করে, মোট 4.5TB লাগবে।"

> **SA_Asraf:**
> "আমি হলে তো এখনই Server বানাতে শুরু করতাম।"

> **DevOps_Taj:**
> "Asraf ভাই, ওভাবে করলে পরে সমস্যা হবে। আমাদের একটা Process মেনে চলা দরকার — SDLC।"

> **Infra_Babu:**
> "SDLC আবার কী জিনিস?"

> **DevOps_Taj:**
> "একটা Standard পদ্ধতি, যেটাতে ৬টা ধাপ থাকে। প্রতিটা ধাপ শেষ করেই পরের ধাপে যেতে হয়।"

---

# 💡 Scene 3: SDLC কী?

```text
═══════════════════════════════════════════════════════════════
SDLC - 6 ধাপ
═══════════════════════════════════════════════════════════════

1️⃣ PLANNING   → কী দরকার সেটা বোঝা
2️⃣ DEFINE     → বুঝে যা বোঝা গেল সেটা লিখে ফেলা
3️⃣ DESIGN     → কীভাবে বানাবো, তার নকশা (HLD + LLD)
4️⃣ BUILD ⭐    → আসল Infrastructure তৈরি
5️⃣ TEST ⭐     → Live করার আগে Staging-এ পরীক্ষা
6️⃣ DEPLOY ⭐   → Production-এ ছাড়া

⭐ = Infrastructure DevOps-এর কাজের জায়গা
```

> **SA_Asraf:**
> "আমি তো সাধারণত শেষ ২-৩টা ধাপই করতাম!"

> **NetMan_Khalid:**
> "যেই ধাপগুলো বাদ দাও, সেগুলোই পরে সমস্যা হয়ে ফিরে আসে।"

---

# 📋 Scene 4: Planning ও Define

> **NetMan_Khalid:**
> "ধাপ ১: Planning।"

```text
═══════════════════════════════════════════════════════════════
PLANNING
═══════════════════════════════════════════════════════════════

দরকার        : 90 দিনের Log রাখা
প্রতিদিনের Log : আনুমানিক 50GB
মোট হিসাব     : প্রায় 4.5TB
কোন টিম জড়িত  : Firewall, Application Server, Database
```

> **Compliance_Rassell:**
> "এখন দরকারটা পরিষ্কার হলো।"

> **NetMan_Khalid:**
> "ধাপ ২: Define। মানে এটাকে লিখিতভাবে নথিভুক্ত করা।"

```text
═══════════════════════════════════════════════════════════════
DEFINE (IRD)
═══════════════════════════════════════════════════════════════

Storage    : আনুমানিক 4.5TB (এখনো আনুমানিক, চূড়ান্ত না)
Security   : Encryption থাকবে
Access     : শুধু SOC Team আর Compliance Team
Retention  : 90 দিন, তারপর Auto Delete
```

---

# 🏗️ Scene 5: Design — এখানেই আসল হিসাব বদলাল

> **NetMan_Khalid:**
> "ধাপ ৩: Design।"

```text
═══════════════════════════════════════════════════════════════
HLD (উঁচু থেকে দেখা Design)
═══════════════════════════════════════════════════════════════

Firewall → Log Collection → Storage → Monitoring Dashboard
```

Design-এর কাজ করতে গিয়ে **Infra_Babu** একটা জিনিস ধরল।

> **Infra_Babu:**
> "Khalid ভাই, একটা সমস্যা। 4.5TB হিসাবটা শুধু Raw Log-এর জন্য। কিন্তু Encryption আর একটা Backup Copy রাখলে, real দরকার হবে প্রায় 6TB। Define-এর সংখ্যাটা বদলাতে হবে।"

> **NetMan_Khalid:**
> "ভালো ধরেছো। এই জন্যই Design ধাপটা গুরুত্বপূর্ণ — Planning-এর হিসাব সব সময় শেষ কথা না।"

```text
═══════════════════════════════════════════════════════════════
LLD (বিস্তারিত Design) — আপডেট হওয়ার পর
═══════════════════════════════════════════════════════════════

Storage    : ~6TB (Encryption + Backup ধরে)
Retention  : 90 দিন
Access     : শুধু Write Permission, Delete না
Dashboard  : আলাদা Monitoring Tool দিয়ে দেখা হবে
```

---

## 💡 Learning Point

Planning-এ যা হিসাব করা হয়, সেটা Design-এ গিয়ে বদলাতেই পারে।

এইজন্যই ধাপ বাদ দেওয়া যায় না — বাদ দিলে এই ভুলটা ধরাই পড়ত না।

---

# 🔧 Scene 6: Build Phase

> **NetMan_Khalid:**
> "ধাপ ৪: Build। এখান থেকে Infrastructure DevOps-এর আসল কাজ শুরু।"

```text
═══════════════════════════════════════════════════════════════
BUILD
═══════════════════════════════════════════════════════════════

কী কী লাগবে
• Infrastructure বানানোর Tool (যেমন Terraform)
• Setting/Config বসানোর Tool (যেমন Ansible)
• কাজের হিসাব রাখার জন্য Version Control (Git)

ধাপগুলো
1. Storage আর Server-এর Configuration লেখা
2. সেই Configuration Apply করা
3. কাজটা Git-এ Push করে রাখা, যাতে পরে দেখা যায় কী বদলেছে
```

---

# 🧪 Scene 7: Test Phase — এবার একটা জিনিস কাজ করেনি

```text
═══════════════════════════════════════════════════════════════
TEST CHECKLIST
═══════════════════════════════════════════════════════════════

☑ Log ঠিকমতো আসছে?
☑ 90 দিন Retention কাজ করছে?
☐ Dashboard Alert ঠিকমতো আসছে?
☑ Storage-এ জায়গা যথেষ্ট আছে?
```

> **NOC_Jahid:**
> "Log আসছে, Retention-ও ঠিক আছে। কিন্তু Dashboard-এ Alert আসছে না, Storage 80% ভরে গেলেও কোনো Notification পাইনি।"

> **DevOps_Taj:**
> "দেখছি। ... আসলে Alert-এর Threshold Setting ভুল বসানো ছিল। ঠিক করলাম।"

(কিছুক্ষণ পর টেস্ট আবার চালানো হলো)

> **NOC_Jahid:**
> "এবার Alert ঠিকমতো এসেছে। সব চেকলিস্ট Pass।"

---

## 💡 Learning Point

Test Phase-এর কাজই হলো এই ধরনের ছোট ভুল Production-এ যাওয়ার আগে ধরা।

যদি এটা এখানে না ধরা পড়ত, তাহলে Storage ভরে গেলেও কেউ জানতে পারত না।

---

# 🚀 Scene 8: Deploy Phase

```text
═══════════════════════════════════════════════════════════════
DEPLOY
═══════════════════════════════════════════════════════════════

1. Infrastructure Apply       → Resource তৈরি হলো
2. Configuration চালানো        → Setting বসলো
3. Smoke Test                 → ঠিকঠাক চলছে কিনা, দ্রুত চেক ✅
4. Monitoring চালু             → Alert এবার সচল
5. Compliance Sign-off         → Production-এ ছাড়ার অনুমতি ✅
```

> **Compliance_Rassell:**
> "90 দিন Retention Confirm। Storage হিসাবও ঠিকমতো আপডেট হয়েছে। Sign off দিচ্ছি।"

---

# ✅ Scene 9: ফলাফল

```text
═══════════════════════════════════════════════════════════════
আগে (SDLC ছাড়া) vs পরে (SDLC মেনে)
═══════════════════════════════════════════════════════════════

আগে
❌ যা মনে আসে তাই শুরু করে দেওয়া
❌ পরে বোঝা যেত হিসাব ভুল ছিল, আবার কাজ করতে হতো
❌ Compliance ধরা পড়লে সমস্যা হতো

পরে
✅ শুরুতেই দরকারটা লিখে রাখা হয়েছে
✅ Design-এ ভুল হিসাব ধরা পড়েছে, আগেভাগেই ঠিক হয়েছে
✅ Test-এ Alert-এর সমস্যা ধরা পড়েছে, Production-এ যাওয়ার আগেই
✅ Compliance Pass করেছে
```

> **NetMan_Khalid:**
> "Centralized Logging System Ready। 90 দিন Retention এখন Active, আর হিসাবও সঠিক।"

---

# 🗣️ Interview Q&A

**Q1. SDLC কী?**
৬ ধাপের একটা Process — Planning, Define, Design, Build, Test, Deploy। প্রতিটা ধাপ পরেরটার ভিত্তি তৈরি করে।

**Q2. Infrastructure DevOps সাধারণত কোন ধাপে কাজ করে?**
Build, Test, Deploy — কিন্তু Design-এর হিসাবও তাদের জানা দরকার, কারণ ওখানেই আসল Number ঠিক হয়।

**Q3. HLD এবং LLD-এর পার্থক্য কী?**

| HLD | LLD |
|---|---|
| বড় ছবি — কী কী অংশ থাকবে | প্রতিটা অংশের বিস্তারিত Setting |
| Overview | Configuration-level Detail |

**Q4. Planning বা Design বাদ দিলে কী হয়?**
হিসাব ভুল থেকে যেতে পারে (যেমন এই Episode-এ Storage কম হিসাব হয়েছিল), যেটা পরে ধরা পড়লে আবার কাজ করতে হয় বা Compliance সমস্যা হয়।

---

# 🎯 Self Introduction (MAC Matrix)

```text
1. Hello, আমি MAC Matrix।
2. আমি Infrastructure DevOps Engineer।
3. SDLC-এর ৬টা ধাপ মেনে কাজ করি।
4. Build, Test আর Deploy-এ সরাসরি কাজ করি।
5. Design-এর হিসাবও ভালো করে বুঝে নিই, যাতে Build-এ ভুল না হয়।
6. Security, Compliance, Audit — সব মাথায় রেখে কাজ করি।
```

---

# 📌 5 Easy Takeaways

```text
1. SDLC = ৬ ধাপ:
   Planning → Define → Design → Build → Test → Deploy

2. Design ধাপে Planning-এর হিসাব বদলাতে পারে —
   এটা ভুল না, এটাই কাজ করার নিয়ম।

3. Test ধাপে ছোটখাটো সমস্যা ধরা পড়াটাই স্বাভাবিক,
   প্রথমবারে সব Perfect হবে ভাবাটাই বরং অস্বাভাবিক।

4. HLD = বড় ছবি, LLD = বিস্তারিত Setting।

5. কোনো ধাপ Skip করলে সমস্যা তখনই বোঝা যায় না,
   পরে বড় আকারে ফিরে আসে।
```

---

# 🛠️ Day 02 Tools: কী ব্যবহার করা যায়

এখানে কোনো Tool "সেরা" বলে দেওয়ার বদলে, কোনটা কখন কাজে লাগে সেটাই বেশি গুরুত্বপূর্ণ।

```text
═══════════════════════════════════════════════════════════════
কাজের ধরন অনুযায়ী কিছু সাধারণ পছন্দ
═══════════════════════════════════════════════════════════════

Work Tracking
• Jira — বড় Team, অনেক Ticket হলে ভালো ফিট
• Trello / Asana — ছোট Team বা কম জটিল কাজের জন্য যথেষ্ট হতে পারে
  (কোনটা ভালো তা নির্ভর করে Team-এর সাইজ আর বাজেটের ওপর)

Documentation
• Confluence — Jira-র সাথে ভালো Integrate হয়
• SharePoint — যেসব জায়গায় আগে থেকেই Microsoft 365 Setup আছে,
  সেখানে এটাই সহজ পছন্দ হতে পারে

Incident & Change Management
• ServiceNow — বড় Bank বা Enterprise-এ প্রচলিত, দাম বেশি
• ছোট Team-এর জন্য Simpler Tool ও চলতে পারে

────────────────────────────────────────────

🔄 Optional — n8n দিয়ে Automate করা যায়
• Jira Ticket তৈরি
• Confluence Document আপডেট
• Slack/Email Notification
• Compliance Audit-এর জন্য রিপোর্ট তৈরি

এইগুলো "লাগবেই" এমন না — Team-এর Manual কাজ কমাতে চাইলে ব্যবহার করা যায়।
```

---

# 🧪 Labs

```text
═══════════════════════════════════════════════════════════════
LABS - DAY 02
═══════════════════════════════════════════════════════════════

LAB 01: SDLC_Phases
কাজ    → ৬টা SDLC ধাপ নিজের ভাষায় লিখে বোঝা
Output → এক পাতার Summary

LAB 02: HLD_LLD_Design
কাজ    → HLD আর LLD-এর পার্থক্য নিজে একটা উদাহরণ দিয়ে দেখানো
Output → Comparison Table

LAB 03: Infrastructure_Requirement_Document
কাজ    → Nord Bank-এর জন্য নিজে একটা IRD বানানো
Output → IRD Document (Storage হিসাবসহ, যেন Design-এ কোনো ভুল ধরা পড়লে
          সেটা কীভাবে Document আপডেট করতে হয় তা বোঝা যায়)

LAB 04: Build_Test_Deploy
কাজ    → Build, Test, Deploy ধাপে ঠিক কী কী চেক করা দরকার তার তালিকা বানানো
Output → একটা Checklist, যেখানে অন্তত একটা সম্ভাব্য Failure Case-ও লেখা থাকবে
```

---

# 📖 গল্পের শেষে

> **NetMan_Khalid:**
> "দরকারটা পরিষ্কার হলে কাজ সহজ হয়, কিন্তু Design আর Test ধাপে গিয়ে ভুল ধরা পড়াটাও স্বাভাবিক।"

> **DevOps_Taj:**
> "Build শুরুর আগে Planning আর Design যত ভালো হবে, পরে তত কম সমস্যা হবে।"

> **Compliance_Rassell:**
> "Compliance Pass। Audit-এর জন্য সব Document রেডি।"

---

# ➡️ পরের পর্ব

## **Episode 03 - Virtualization Fundamentals**

Virtualization, Hypervisor, Virtual Machine (VM), Resource Allocation, VMware ESXi, KVM — এইগুলো দিয়ে Nord Bank কীভাবে Hardware খরচ কমায় এবং Infrastructure আরও কার্যকর করে, সেটা পরের Episode-এ।
