# 🏦 Nord Bank - Episode 03: The Server Waste Problem

**📖 Date:** Wednesday, 17 January, 9:30 AM  
**📍 Location:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Problem

**Finance_Arif** দ্রুত **NetMan_Khalid**-এর ডেস্কে এলেন। হাতে একটি Excel Sheet।

> **Finance_Arif:**  
> "Khalid ভাই! IT Cost বেড়ে যাচ্ছে! দেখেন, গত Quarter-এ 15টা Physical Server কেনা হয়েছে!"

> **NetMan_Khalid:**  
> "15টা Server? এত কেন?"

> **Finance_Arif:**  
> "প্রতিটা Team আলাদা Server চায়! Application Support Team ১টা, DevOps Team ১টা, SOC Team ১টা... এভাবে 15টা!"

> **NetMan_Khalid:**  
> "কিন্তু তাদের আসলে কত Resource দরকার?"

> **Finance_Arif:**  
> "Application Support Team-এর দরকার মাত্র 8GB RAM আর 4 CPU Core। কিন্তু পুরো 128GB RAM-এর Server দেওয়া হয়েছে!"

> **NetMan_Khalid:**  
> "মানে 120GB RAM নষ্ট! এটাই তো আসল Problem!"

---

# 🏢 Scene 2: The Meeting

> **NetMan_Khalid:**  
> "Team! Finance বলছে Cost বেড়ে যাচ্ছে। সবাই আলাদা Physical Server চাইছে, কিন্তু Resource Waste হচ্ছে।"

> **Infra_Babu:**  
> "Enterprise-এ আগে এভাবেই করা হতো।"

> **DevOps_Taj:**  
> "কিন্তু Babu ভাই! 128GB RAM-এর Server-এ যদি 8GB ব্যবহার হয়, তাহলে বাকি সব Resource নষ্ট!"

> **NetMan_Khalid:**  
> "এই Problem-এর Solution হলো Virtualization।"

> **SA_Asraf:**  
> "Virtualization কী?"

---

# 💡 Scene 3: What is Virtualization?

> **NetMan_Khalid:**  
> "Virtualization মানে একটি Physical Server-কে ভাগ করে একাধিক Virtual Machine (VM) তৈরি করা।"

```text
═══════════════════════════════════════════════════════════════
PHYSICAL SERVER → VIRTUALIZATION → MULTIPLE VM
═══════════════════════════════════════════════════════════════

Physical Server
64GB RAM
16 CPU Core

        │
        ▼

 HYPERVISOR (Software)

        │

 ┌──────┼──────┐
 ▼      ▼      ▼

 VM1    VM2    VM3

 8GB    8GB    16GB
4 Core 4 Core 4 Core
```

> **SA_Asraf:**  
> "একটা Physical Server থেকে এতগুলো VM?"

> **DevOps_Taj:**  
> "হ্যাঁ! Hypervisor নামের Software এটা করে।"

> **Finance_Arif:**  
> "তাহলে Cost কেমন কমে?"

> **NetMan_Khalid:**  
> "15টা Server-এর বদলে মাত্র 3-4টা Server-এ সব কাজ হয়ে যায়।"

---

# 🔧 Scene 4: Hypervisor Explained

> **NetMan_Khalid:**  
> "Hypervisor-এর তিনটি প্রধান কাজ আছে।"

```text
═══════════════════════════════════════════════════════════════
HYPERVISOR - 3 MAIN TASKS
═══════════════════════════════════════════════════════════════

1. RESOURCE ALLOCATION

   VM-কে CPU ও RAM বরাদ্দ দেয়

────────────────────────────────────────────

2. ISOLATION

   একটি VM অন্য VM-এর Data Access করতে পারে না

────────────────────────────────────────────

3. MANAGEMENT

   VM Create
   VM Start
   VM Stop
   VM Delete
```

> **Security_Shahed:**  
> "Isolation Banking Sector-এ খুবই গুরুত্বপূর্ণ!"

> **DevOps_Taj:**  
> "Hypervisor আবার দুই ধরনের।"

```text
═══════════════════════════════════════════════════════════════
TYPE 1 vs TYPE 2 HYPERVISOR
═══════════════════════════════════════════════════════════════

TYPE 1 (BARE-METAL)

✔ Hardware-এর উপর সরাসরি চলে

✔ Performance বেশি

✔ Enterprise Production

Examples

• VMware ESXi

• KVM

────────────────────────────────────────────

TYPE 2 (HOSTED)

✔ Operating System-এর উপর চলে

✔ Performance কম

✔ Testing ও Lab-এর জন্য

Example

• VirtualBox
```

> **Infra_Babu:**  
> "Nord Bank-এ কোনটা ব্যবহার হবে?"

> **NetMan_Khalid:**  
> "Production Environment-এ সবসময় Type-1 Hypervisor।"

---

# 🏛️ Scene 5: Hypervisor Recommendation

```text
═══════════════════════════════════════════════════════════════
RECOMMENDED HYPERVISOR
═══════════════════════════════════════════════════════════════

✅ VMware ESXi

Enterprise Standard

Suitable for Banking

────────────────────────────────────────────

✅ KVM

Open Source

Free

Cost Effective
```

> **Finance_Arif:**  
> "কোনটা নেব?"

> **NetMan_Khalid:**  
> "Nord Bank-এর জন্য VMware ESXi ভালো Option।"

> **SA_Asraf:**  
> "KVM তো Free!"

> **NetMan_Khalid:**  
> "ঠিক, কিন্তু VMware-এ vMotion, High Availability (HA), এবং DRS-এর মতো Enterprise Feature আছে।"

---

# 📋 Scene 6: Resource Allocation Plan

> **NetMan_Khalid:**  
> "চলুন Resource Allocation Plan দেখি।"

```text
═══════════════════════════════════════════════════════════════
RESOURCE ALLOCATION PLAN
═══════════════════════════════════════════════════════════════

Physical Server

64GB RAM

16 CPU Core

────────────────────────────────────────────

Application Support

8GB RAM

4 Core

────────────────────────────────────────────

DevOps Team

8GB RAM

4 Core

────────────────────────────────────────────

SOC Team

16GB RAM

4 Core

────────────────────────────────────────────

NOC Team

8GB RAM

2 Core

────────────────────────────────────────────

TOTAL REQUIRED

RAM : 40GB

CPU : 14 Core

────────────────────────────────────────────

AVAILABLE

RAM : 64GB

CPU : 16 Core

────────────────────────────────────────────

BUFFER

24GB RAM

2 CPU Core

37.5% Free Capacity ✅
```

> **Infra_Babu:**  
> "এই Buffer Unexpected Load Handle করবে।"

> **Security_Shahed:**  
> "VM Isolation ঠিক আছে?"

> **NetMan_Khalid:**  
> "VMware ESXi Strong Isolation দেয়।"

---

# ☁️ Scene 7: AWS EC2 Connection *(Day 04 Preview)*

> **DevOps_Taj:**  
> "Khalid ভাই! AWS EC2-ও তো আসলে Virtual Machine!"

> **NetMan_Khalid:**  
> "একদম ঠিক!"

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

Nitro Hypervisor
(KVM Based)

        │

 ┌──────┼──────┐
 ▼      ▼      ▼

EC2    EC2    EC2
```

> **SA_Asraf:**  
> "On-Premises-এ VMware আর Cloud-এ EC2, দুটোই Virtualization!"

---

# ✅ Scene 8: The Result

```text
═══════════════════════════════════════════════════════════════
BEFORE vs AFTER
═══════════════════════════════════════════════════════════════

BEFORE

• 15 Physical Servers

• 70-80% Resource Waste

• High Cost

• 10-15 Days Provisioning

────────────────────────────────────────────

AFTER

• 3-4 Physical Servers

• 60-70% Resource Utilization

• 40-50% Cost Saving

• Provisioning in Hours
```

> **Finance_Arif:**  
> "40-50% Cost Saving! CEO অনেক খুশি হবে!"

---

# 🗣️ Interview Q&A

### Q1. Virtualization কী?

**Answer**

একটি Physical Server-কে ভাগ করে একাধিক Virtual Machine (VM) তৈরি করার প্রযুক্তি।

---

### Q2. Hypervisor কী?

**Answer**

Hypervisor হলো সেই Software যা Virtual Machine তৈরি ও পরিচালনা করে।

---

### Q3. Type-1 এবং Type-2 Hypervisor-এর পার্থক্য কী?

| Type-1 | Type-2 |
|---------|---------|
| Hardware-এর উপর চলে | Operating System-এর উপর চলে |
| Enterprise Production | Testing & Learning |
| High Performance | Lower Performance |
| VMware ESXi, KVM | VirtualBox |

---

### Q4. Banking Sector-এর জন্য কোন Hypervisor?

**Answer**

**VMware ESXi** হলো Enterprise Standard।

---

### Q5. Buffer কেন রাখা হয়?

**Answer**

Unexpected Workload Handle করার জন্য।

---

# 🎯 Self Introduction (MAC Matrix)

```text
1. Hello, আমি MAC Matrix.

2. আমি Infrastructure DevOps Engineer.

3. Physical Server থেকে Virtualization Platform-এ কাজ করি.

4. VMware ESXi এবং KVM সম্পর্কে জানি.

5. Resource Allocation Plan তৈরি করতে পারি.

6. Buffer Planning এবং Capacity Management বুঝি.

7. AWS EC2-ও একটি Virtual Machine — এটি Day 04-এ বিস্তারিত শিখব।
```

---

# 📌 5 Easy Takeaways

```text
1.

Virtualization

Physical Server

↓

Multiple Virtual Machines

────────────────────────────

2.

Hypervisor

=

Virtualization Engine

────────────────────────────

3.

Type-1

Production

Type-2

Testing

────────────────────────────

4.

VMware ESXi

=

Enterprise Banking Standard

────────────────────────────

5.

Always Keep Resource Buffer

For Future Growth
```

---

# 🛠️ Day 03 Tools: What to Use & What to Skip

```text
═══════════════════════════════════════════════════════════════
DAY 03 - TOOLS: USE ✅ vs SKIP ❌
═══════════════════════════════════════════════════════════════

✅ USE (Industry Standard)

1. VMware ESXi

Enterprise Standard

────────────────────────────────────────────

2. KVM

Open Source

Free

────────────────────────────────────────────

❌ SKIP

1. Hyper-V

Windows Specific

────────────────────────────────────────────

2. Xen

Older Technology

────────────────────────────────────────────

3. VirtualBox

Type-2 Hypervisor

Production-এর জন্য নয়

────────────────────────────────────────────

🔄 OPTIONAL (Advanced)

n8n

• VM Resource Monitoring

• VM Health Notifications

• VM Creation Workflow

• Resource Utilization Reports
```

---

# 🧪 Labs

```text
═══════════════════════════════════════════════════════════════
LABS - DAY 03
═══════════════════════════════════════════════════════════════

LAB 01

Day03_01_Virtualization_Concept

Task

Understand

Physical Server

vs

Virtual Machine

Output

Virtualization Summary

────────────────────────────────────────────

LAB 02

Day03_02_Hypervisor_Types

Task

Compare

Type-1

vs

Type-2

Output

Comparison Table

────────────────────────────────────────────

LAB 03

Day03_03_Resource_Allocation_Plan

Task

Create Resource Allocation Plan

64GB RAM

16 CPU Core

Output

Planning Document

────────────────────────────────────────────

LAB 04

Day03_04_Hypervisor_Comparison

Task

Compare

VMware ESXi

vs

KVM

Output

Comparison Report
```

---

# 📖 Story Ending

> **NetMan_Khalid:**  
> "একটি Physical Server-এর সর্বোচ্চ ব্যবহার করতে হলে Virtualization অপরিহার্য।"

> **Finance_Arif:**  
> "কম Server, কম Cost, বেশি Efficiency!"

> **DevOps_Taj:**  
> "আজ Virtualization শিখলাম। কাল Cloud-এর EC2 দেখব।"

```text
🎉 THE END 🎉

Virtualization

✔ Better Resource Utilization

✔ Lower Infrastructure Cost

✔ Faster Provisioning

✔ Better Scalability

✔ Enterprise Ready
```

---

# ⬅️ Previous Episode

## **Day 02 - Enterprise SDLC**

---

# ➡️ Next Episode

## **Day 04 - AWS EC2**