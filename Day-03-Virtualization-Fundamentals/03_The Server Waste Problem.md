# 🏦 Nord Bank - Episode 03: Virtualization Fundamentals

**📖 তারিখ:** Wednesday, 17 January, 9:30 AM
**📍 স্থান:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Cost Problem

Finance_Arif হাতে একটা Excel Sheet নিয়ে NetMan_Khalid-এর ডেস্কে এলেন।

> **Finance_Arif:**
> "Khalid ভাই, IT Cost বেড়ে যাচ্ছে। গত Quarter-এ 15টা Physical Server কেনা হয়েছে।"

> **NetMan_Khalid:**
> "15টা? কারণ কী?"

> **Finance_Arif:**
> "প্রতিটা Team আলাদা Server চায়। Application Support Team চায় 1টা, DevOps Team চায় 1টা — এভাবে মোট 15টা।"

> **NetMan_Khalid:**
> "কিন্তু তাদের আসলে কত লাগে?"

> **Finance_Arif:**
> "Application Support Team-এর দরকার 8GB RAM, 4 Core। কিন্তু তারা পেয়েছে পুরো একটা 128GB RAM-এর Server।"

> **NetMan_Khalid:**
> "মানে 120GB RAM অলস পড়ে আছে। এটা বড় সমস্যা।"

---

# 🏢 Scene 2: The Meeting

> **NetMan_Khalid:**
> "Team, শোনো। প্রতি Team আলাদা Physical Server চাইছে, কিন্তু বেশিরভাগ Resource ব্যবহারই হচ্ছে না।"

> **Infra_Babu:**
> "আগে এটাই তো নিয়ম ছিল — এক Team, এক Server।"

> **DevOps_Taj:**
> "কিন্তু Babu ভাই, 128GB-র Server-এ মাত্র 8GB ব্যবহার হচ্ছে। বাকিটা শুধু বসে থাকছে।"

> **NetMan_Khalid:**
> "এর সমাধান — Virtualization।"

> **SA_Asraf:**
> "Virtualization তো চিনি, আগে ছোট scale-এ কাজ করেছি। কিন্তু Bank-এর মতো জায়গায় Production-এ পুরোপুরি ভরসা করা যায়? মানে একটা Physical Server Down হলে তো একসাথে অনেকগুলো Team-এর কাজ বন্ধ হয়ে যাবে।"

> **NetMan_Khalid:**
> "ভালো প্রশ্ন। এটাই আসলে সবচেয়ে গুরুত্বপূর্ণ বিষয় — একা Virtualization যথেষ্ট না, তার সাথে High Availability দরকার। সেটাও বলছি।"

---

## 💡 Learning Point

Virtualization মানে শুধু Resource বাঁচানো না।

একটা Physical Server-এর ওপর একাধিক Team নির্ভর করলে, সেই Server Down হওয়ার ঝুঁকিও মাথায় রাখতে হয়।

---

# 💡 Scene 3: Virtualization কী?

> **NetMan_Khalid:**
> "Virtualization মানে একটা Physical Server-কে ভাগ করে একাধিক Virtual Machine (VM) বানানো।"

```text
═══════════════════════════════════════════════════════════════
PHYSICAL SERVER → HYPERVISOR → MULTIPLE VM
═══════════════════════════════════════════════════════════════

Physical Server (64GB RAM, 16 Core CPU)
         │
         ▼
   HYPERVISOR (Software)
         │
    ┌────┼────┐
    ▼    ▼    ▼
  VM1   VM2   VM3
 8GB    8GB   16GB
 4Core  4Core  4Core
```

> **Finance_Arif:**
> "Cost-এ কী পার্থক্য হবে?"

> **NetMan_Khalid:**
> "15টা Server-এর কাজ 3-4টা Server দিয়ে হবে। কিন্তু ঠিক কত Cost কমবে, সেটা হিসাব করে দেখাবো — শুধু ধারণা থেকে বলব না।"

---

# 🔧 Scene 4: Hypervisor

> **NetMan_Khalid:**
> "Hypervisor-এর ৩টা প্রধান কাজ —"

```text
═══════════════════════════════════════════════════════════════
HYPERVISOR - 3 কাজ
═══════════════════════════════════════════════════════════════

1. RESOURCE ALLOCATION → কোন VM কত CPU/RAM পাবে
2. ISOLATION           → এক VM অন্য VM-এর Data দেখতে পারবে না
3. MANAGEMENT          → VM Create, Start, Stop, Delete
```

> **Security_Shahed:**
> "Isolation কতটা শক্ত? মানে একটা VM যদি Compromise হয়, অন্য VM-এ ছড়াতে পারবে না তো?"

> **NetMan_Khalid:**
> "সাধারণত পারে না — এটাকে বলে VM Escape, এবং এটা খুবই বিরল। কিন্তু 'অসম্ভব' বলা ঠিক না। এই জন্যই Patch আপডেট রাখা আর Hypervisor নিজেই Secure রাখা জরুরি।"

> **DevOps_Taj:**
> "Hypervisor দুই ধরনের —"

```text
═══════════════════════════════════════════════════════════════
TYPE 1 vs TYPE 2
═══════════════════════════════════════════════════════════════

TYPE 1 (BARE-METAL)
├── সরাসরি Hardware-এর উপর চলে
├── Performance ভালো
├── Production/Enterprise-এ ব্যবহার হয়
└── উদাহরণ: VMware ESXi, KVM

TYPE 2 (HOSTED)
├── একটা OS-এর উপরে চলে
├── Performance তুলনামূলক কম
├── সাধারণত Testing বা শেখার জন্য
└── উদাহরণ: VirtualBox, VMware Workstation
```

> **Infra_Babu:**
> "Nord Bank-এ কোনটা?"

> **NetMan_Khalid:**
> "Production-এ Type 1। Type 2 আমরা শুধু নিজেদের Laptop-এ Practice বা ছোট Test করার জন্য রাখব — সরাসরি Bank-এর আসল কাজে না।"

---

# 🏛️ Scene 5: কোন Hypervisor — এবং কত খরচ

> **NetMan_Khalid:**
> "দুইটা Option — VMware ESXi আর KVM। দুটোই Type 1।"

> **Finance_Arif:**
> "দামের পার্থক্য কত?"

> **NetMan_Khalid:**
> "KVM Open-source, তাই License Cost নেই। VMware ESXi-এর License আর Support Cost আছে — সেটা ছোট খরচ না।"

> **SA_Asraf:**
> "তাহলে Free-টাই নেওয়া উচিত না?"

> **NetMan_Khalid:**
> "সব সময় না। VMware-এ কিছু Feature আছে যেগুলো Banking-এর জন্য দরকারি — যেমন vMotion (একটা Server থেকে অন্য Server-এ VM সরানো Downtime ছাড়াই), আর HA (একটা Server Down হলে অন্য Server VM গুলো তুলে নেয়)। KVM-এও এগুলো করা যায়, কিন্তু Setup করতে বেশি Manual কাজ আর Expertise লাগে।"

> **Finance_Arif:**
> "তাহলে সিদ্ধান্ত কী?"

> **NetMan_Khalid:**
> "Core Banking-সংক্রান্ত আর Critical Workload-এ VMware ESXi — কারণ Downtime-এর ঝুঁকি এখানে বেশি ক্ষতির। কম Critical Workload-এ, যেমন Internal Testing বা Monitoring, KVM ব্যবহার করে খরচ কমানো যায়। পুরোপুরি এক দিকে না গিয়ে ভাগ করে নেওয়াই ভালো।"

> **Finance_Arif:**
> "এইভাবে হলে হিসাবটা লিখে পাঠান, আমি License Cost-এর সাথে মিলিয়ে দেখব।"

---

## 💡 Learning Point

"Best" Tool বলে কিছু হয় না — কোন Workload কতটা Critical, তার ওপর নির্ভর করে Tool বাছাই করতে হয়। শুধু Feature দেখে না, Cost-ও দেখে।

---

# 📋 Scene 6: Resource Allocation Plan

> **NetMan_Khalid:**
> "একটা Physical Server (64GB RAM, 16 Core) দিয়ে হিসাব করি।"

```text
═══════════════════════════════════════════════════════════════
RESOURCE ALLOCATION PLAN
═══════════════════════════════════════════════════════════════

Team-ভিত্তিক দরকার:
├── Application Support : 8GB RAM,  4 Core
├── DevOps Team         : 8GB RAM,  4 Core
├── SOC Team             : 16GB RAM, 4 Core
└── NOC Team             : 8GB RAM,  2 Core
                          ─────────────────
মোট দরকার                : 40GB RAM, 14 Core

সার্ভারে আছে              : 64GB RAM, 16 Core
বাকি থাকছে (Buffer)        : 24GB RAM (37.5%), 2 Core
```

> **Infra_Babu:**
> "37.5% Buffer তো বেশ বড়। এটা কি দরকার, না বেশি?"

> **NetMan_Khalid:**
> "ভালো প্রশ্ন। সাধারণ নিয়ম হলো 15-20% Buffer রাখা, Unexpected Load-এর জন্য। এখানে হিসাব করে 37.5% এসেছে কারণ আমরা একটা মাঝারি সাইজের Server ধরে হিসাব করেছি। এত বড় Buffer মানে এই Server-এ আরও একটা Team-এর কাজও নেওয়া যেতে পারে — এটা Waste না, বরং ভবিষ্যতের জন্য জায়গা।"

> **Security_Shahed:**
> "Isolation ঠিক থাকলে সমস্যা নেই।"

---

# ☁️ Scene 7: AWS EC2 আসলে VM

> **DevOps_Taj:**
> "Khalid ভাই, AWS EC2 আসলে একটা VM।"

> **NetMan_Khalid:**
> "ঠিক। EC2 মানে Virtual Machine, শুধু AWS নিজেই সেই Hypervisor চালায় আর মেইনটেইন করে।"

```text
═══════════════════════════════════════════════════════════════
AWS EC2 = VIRTUAL MACHINE
═══════════════════════════════════════════════════════════════

AWS Data Center → Physical Server → Nitro Hypervisor (KVM-based)
                                          │
                                    ┌─────┼─────┐
                                    ▼     ▼     ▼
                                  EC2   EC2   EC2
```

> **SA_Asraf:**
> "তাহলে On-Premise-এ VMware, Cloud-এ EC2 — দুই জায়গাতেই আসলে একই ধারণা, শুধু কে চালাচ্ছে সেটা আলাদা।"

> **NetMan_Khalid:**
> "ঠিক ধরেছো।"

---

# ✅ Scene 8: ফলাফল

```text
═══════════════════════════════════════════════════════════════
আগে vs পরে
═══════════════════════════════════════════════════════════════

আগে (Physical Server)
├── 15টা Physical Server
├── বেশিরভাগ Resource অব্যবহৃত
├── খরচ বেশি
└── নতুন Server বসাতে 10-15 দিন

পরে (Virtualization)
├── 3-4টা Physical Server
├── Resource ব্যবহার অনেক বেড়েছে
├── License + Hardware মিলিয়ে হিসাব করে খরচ কমেছে,
   ঠিক সংখ্যা Finance_Arif-এর হিসাবের পর চূড়ান্ত হবে
└── নতুন VM বানাতে লাগে ঘণ্টাখানেক
```

> **Finance_Arif:**
> "প্রাথমিক হিসাবে ভালো লাগছে। চূড়ান্ত সংখ্যা লিখিত রিপোর্টে দেখে তারপর CEO-কে জানাব।"

---

## 💡 Learning Point

এই গল্পে ইচ্ছা করেই কোনো নির্দিষ্ট "% cost saving" এর সংখ্যা চূড়ান্ত করে দেওয়া হয়নি।

বাস্তবে License Cost, Hardware Cost, আর Team-এর সময় — সব মিলিয়ে হিসাব করার পরই আসল সংখ্যা পাওয়া যায়। শুধু অনুমান করে "40-50% কমবে" বলাটা বাস্তবসম্মত না।

---

# 🗣️ Interview Q&A

**Q1. Virtualization কী?**
একটা Physical Server-কে ভাগ করে একাধিক VM বানানো, যাতে Resource-এর অপচয় কম হয়।

**Q2. Hypervisor কী?**
যে Software VM তৈরি, পরিচালনা এবং Isolate করে।

**Q3. Type-1 vs Type-2?**
Type-1 সরাসরি Hardware-এ চলে, Production-এ ব্যবহার হয় (যেমন VMware ESXi, KVM)। Type-2 একটা OS-এর উপর চলে, সাধারণত Testing বা শেখার জন্য (যেমন VMware Workstation)।

**Q4. VMware নাকি KVM?**
নির্ভর করে Workload কতটা Critical তার ওপর। Critical/Core Workload-এ VMware-এর মতো Enterprise Feature কাজে লাগে; কম Critical কাজে KVM দিয়ে খরচ কমানো যায়। শুধু Feature দেখে না, License Cost-ও হিসাবে রাখতে হয়।

**Q5. Buffer কেন রাখা হয়?**
Unexpected Load সামলাতে। সাধারণ নিয়ম 15-20%, তবে হিসাব-ভেদে এর কমবেশি হতে পারে — সংখ্যাটা মুখস্থ না করে, কেন রাখা হচ্ছে সেটা বোঝা জরুরি।

---

# 🎯 Self Introduction (MAC Matrix)

```text
1. হ্যালো, আমি MAC Matrix, Infrastructure DevOps Engineer।
2. Physical Server থেকে Virtualization-এ কাজ করি।
3. VMware ESXi আর KVM — দুটোই বুঝি, কোনটা কখন লাগে সেটা জানি।
4. Resource Allocation Plan বানাই, আর কেন Buffer লাগে সেটা ব্যাখ্যা করতে পারি।
5. AWS EC2-ও যে আসলে একটা VM, সেটা বুঝি।
```

---

# 📌 5 Takeaways

```text
1. Virtualization = এক Physical Server → একাধিক VM

2. Hypervisor-ই সব VM-এর Resource, Isolation, আর
   Management সামলায়।

3. Type-1 = Production, Type-2 = Testing/Learning।

4. Tool বাছাই = Workload-এর গুরুত্ব + Cost — দুটোই দেখে,
   শুধু Feature List দেখে না।

5. Buffer সাধারণত 15-20%, কিন্তু আসল সংখ্যা নির্ভর করে
   আসল হিসাবের ওপর — কোনো একটা ফিক্সড রুল মুখস্থ না করে
   হিসাবটা কীভাবে করে সেটা বোঝা জরুরি।
```

---

# 🖥️ Hands-On Labs - Day 03

> **Note:** Production-এ Nord Bank VMware ESXi (Type-1) ব্যবহার করে। কিন্তু বাস্তবে  নিজের Laptop-এ Bare-metal Server বসানো সম্ভব না। তাই Practice করার জন্য VMware Workstation (Type-2) ব্যবহার হবে — concept একই থাকে, শুধু চালানোর জায়গাটা আলাদা।

```text
═══════════════════════════════════════════════════════════════
HANDS-ON LABS - DAY 03
═══════════════════════════════════════════════════════════════

LAB 01: VMware_Workstation_Setup
কাজ    → VMware Workstation-এ একটা Test VM বানাতে হবে (Ubuntu Server)
Output → VM তৈরি হয়ে চলছে

LAB 02: Resource_Allocation_Plan
কাজ    → Nord Bank-এর 64GB RAM, 16 Core Server-এর জন্য নিজে একটা
          Resource Allocation Plan বানাতে হবে, Buffer-সহ
Output → Resource Allocation Plan Document, সাথে Buffer কেন
          এই পরিমাণ রাখা হলো তার একটা ছোট ব্যাখ্যা
```

---

# 🎉 THE END 🎉

```text
📌 PREVIOUS: 02_Episode_Enterprise_SDLC
📌 NEXT: 04_Episode_AWS_EC2
```
