# 🏦 Nord Bank - Episode 03: The Server Waste Problem

**📖 Date:** Wednesday, 17 January, 9:30 AM  
**📍 Location:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Problem

**Finance_Arif** হাতে একটি Excel Sheet নিয়ে **NetMan_Khalid**-এর ডেস্কে এলেন।

> **Finance_Arif:**  
> "Khalid ভাই! IT Cost বেড়ে যাচ্ছে! দেখেন — গত Quarter-এ 15টা Physical Server কেনা হয়েছে!"

> **NetMan_Khalid:**  
> "15টা Server? এত কেন?"

> **Finance_Arif:**  
> "প্রতিটা Team আলাদা Server চায়! Application Support Team চায় 1টা, DevOps Team চায় 1টা — এভাবে 15টা!"

> **NetMan_Khalid:**  
> "কিন্তু তাদের কত Resource দরকার?"

> **Finance_Arif:**  
> "Application Support Team-এর দরকার 8GB RAM, 4 Core। কিন্তু তারা পেয়েছে পুরো 128GB RAM-এর Server!"

> **NetMan_Khalid:**  
> "বাকি 120GB RAM নষ্ট! এটা বড় Problem!"

---

# 🏢 Scene 2: The Meeting

> **NetMan_Khalid:**  
> "Team! Finance_Arif বলছে Cost বেড়ে যাচ্ছে। প্রতি Team আলাদা Physical Server চায়। কিন্তু Resource Waste হচ্ছে!"

> **Infra_Babu:**  
> "Enterprise-এ এটাই Standard Practice ছিল!"

> **DevOps_Taj:**  
> "কিন্তু Babu ভাই! 128GB RAM-এর Server-এ মাত্র 8GB ব্যবহার হচ্ছে। বাকি 120GB নষ্ট!"

> **NetMan_Khalid:**  
> "এই Problem-এর Solution হলো **Virtualization**।"

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
16 Core CPU

        │
        ▼

   Hypervisor

        │
 ┌──────┼──────┐
 ▼      ▼      ▼

 VM1    VM2    VM3

8GB     8GB    16GB
4 Core  4 Core 4 Core
```

> **SA_Asraf:**  
> "একটা Physical Server থেকে একাধিক VM?"

> **DevOps_Taj:**  
> "হ্যাঁ। Hypervisor নামে Software এটা করে।"

> **Finance_Arif:**  
> "Cost কেমন হয়?"

> **NetMan_Khalid:**  
> "15টা Server-এর বদলে 3-4টা Server-এ সব কাজ হয়ে যায়। Cost অনেক কমে।"

---

# 🔧 Scene 4: Hypervisor Explained

> **NetMan_Khalid:**  
> "Hypervisor-এর 3টি প্রধান কাজ আছে।"

```text
═══════════════════════════════════════════════════════════════
HYPERVISOR - 3 MAIN TASKS
═══════════════════════════════════════════════════════════════

1. RESOURCE ALLOCATION

   └── কোন VM কত CPU ও RAM পাবে

────────────────────────────────────────────

2. ISOLATION

   └── এক VM অন্য VM-এর Data Access করতে পারবে না

────────────────────────────────────────────

3. MANAGEMENT

   ├── Create VM
   ├── Start VM
   ├── Stop VM
   └── Delete VM
```

> **Security_Shahed:**  
> "Isolation খুব গুরুত্বপূর্ণ। Banking Sector-এ Security আগে।"

> **DevOps_Taj:**  
> "Hypervisor আবার দুই ধরনের।"

```text
═══════════════════════════════════════════════════════════════
TYPE-1 vs TYPE-2 HYPERVISOR
═══════════════════════════════════════════════════════════════

TYPE-1 (Bare Metal)

✔ Runs directly on Hardware
✔ High Performance
✔ Enterprise Production

Examples

• VMware ESXi
• KVM

────────────────────────────────────────────

TYPE-2 (Hosted)

✔ Runs on Operating System
✔ Lower Performance
✔ Mainly Testing

Example

• Oracle VirtualBox
```

> **Infra_Babu:**  
> "Nord Bank-এ কোনটা?"

> **NetMan_Khalid:**  
> "Type-1। Enterprise Production-এ সবসময় Type-1 ব্যবহার করা হয়।"

---

# 🏛️ Scene 5: Hypervisor Recommendation

```text
═══════════════════════════════════════════════════════════════
RECOMMENDED HYPERVISOR
═══════════════════════════════════════════════════════════════

✅ VMware ESXi
   Enterprise Standard
   Banking Sector

✅ KVM
   Open Source
   Cost Effective

শুধু এই দুইটি শিখলেই যথেষ্ট।
```

> **Finance_Arif:**  
> "কোনটা নেওয়া হবে?"

> **NetMan_Khalid:**  
> "Nord Bank-এর জন্য VMware ESXi সবচেয়ে ভালো Option।"

> **SA_Asraf:**  
> "KVM তো Free। তাহলে VMware কেন?"

> **NetMan_Khalid:**  
> "VMware-এ Enterprise Features আছে।"

- vMotion
- High Availability (HA)
- Distributed Resource Scheduler (DRS)

> "Banking Environment-এ এগুলো খুব গুরুত্বপূর্ণ।"

---

# 📋 Scene 6: Resource Allocation Plan

> **NetMan_Khalid:**  
> "Resource Allocation Plan দেখুন।"

```text
═══════════════════════════════════════════════════════════════
RESOURCE ALLOCATION PLAN
═══════════════════════════════════════════════════════════════

Physical Server

64GB RAM
16 Core CPU

────────────────────────────────────────────

Application Support
8GB RAM
4 Core

DevOps Team
8GB RAM
4 Core

SOC Team
16GB RAM
4 Core

NOC Team
8GB RAM
2 Core

────────────────────────────────────────────

Total Required

RAM : 40GB
CPU : 14 Core

Available

RAM : 64GB
CPU : 16 Core

Buffer

RAM : 24GB (37.5%)

CPU : 2 Core
```

> **Infra_Babu:**  
> "37.5% Buffer থাকলে Unexpected Load Handle করা যাবে।"

> **Security_Shahed:**  
> "VM Isolation ঠিক থাকবে?"

> **NetMan_Khalid:**  
> "VMware ESXi খুব Strong Isolation দেয়।"

---

# ☁️ Scene 7: AWS EC2 Connection

> **DevOps_Taj:**  
> "Khalid ভাই! AWS EC2-ও তো VM!"

> **NetMan_Khalid:**  
> "ঠিকই বলেছো। EC2 আসলে Virtual Machine।"

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
> "On-Premise-এ VMware, Cloud-এ EC2। দুই জায়গাতেই Virtualization!"

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

Physical Server-কে ভাগ করে একাধিক Virtual Machine (VM) তৈরি করা।

---

### Q2. Hypervisor কী?

**Answer**

Hypervisor হলো সেই Software যা Virtual Machine তৈরি ও পরিচালনা করে।

---

### Q3. Type-1 এবং Type-2 Hypervisor-এর পার্থক্য কী?

**Answer**

| Type-1 | Type-2 |
|---------|---------|
| Hardware-এর উপর চলে | Operating System-এর উপর চলে |
| Production Environment | Testing Environment |
| High Performance | Lower Performance |
| VMware ESXi, KVM | Oracle VirtualBox |

---

### Q4. Banking Sector-এর জন্য কোন Hypervisor ভালো?

**Answer**

VMware ESXi

কারণ এতে আছে:

- vMotion
- High Availability (HA)
- DRS
- Enterprise Support

---

### Q5. Buffer কেন রাখা হয়?

**Answer**

Unexpected Load Handle করার জন্য।

---

# 🎯 Self Introduction (MAC Matrix)

```text
1. Hello, আমি MAC Matrix।

2. আমি Infrastructure DevOps Engineer।

3. Physical Server থেকে Virtualization Platform তৈরি করি।

4. VMware ESXi ও KVM নিয়ে কাজ করি।

5. Resource Allocation Plan তৈরি করি এবং Buffer Maintain করি।

6. AWS EC2-ও Virtual Machine — এটা ভালোভাবে বুঝি।
```

---

# 📌 5 Easy Takeaways

```text
1. Virtualization

Physical Server
        ↓
Multiple Virtual Machines

────────────────────────────

2. Hypervisor

Virtualization Engine

────────────────────────────

3. Type-1

Production

Type-2

Testing

────────────────────────────

4. VMware ESXi

Enterprise Banking Standard

────────────────────────────

5. Buffer

Always Keep Extra Resources
(Recommended 10-15% or based on workload planning)
```

---

# 🛠️ Tools: What to Use & What to Skip

```text
═══════════════════════════════════════════════════════════════
TOOLS - DAY 03
═══════════════════════════════════════════════════════════════

✅ USE

1. VMware ESXi
   Enterprise Standard

2. KVM
   Open Source
   Cost Effective

────────────────────────────────────────────

❌ SKIP

1. Hyper-V
   Windows Focused

2. Xen
   Legacy Platform

3. VirtualBox
   Type-2 Hypervisor
   Not for Production

────────────────────────────────────────────

🔄 OPTIONAL (Advanced)

n8n

• VM Health Monitoring

• VM Resource Alerts

• VM Provisioning Workflow

• Resource Utilization Reports
```

---

# 🧪 LAB Scenarios

```text
═══════════════════════════════════════════════════════════════
LABS - DAY 03
═══════════════════════════════════════════════════════════════

LAB 01

Day03_01_Virtualization_Concept

Task

• Physical Server vs VM
• Virtualization Concept

Output

Virtualization Summary

────────────────────────────────────────────

LAB 02

Day03_02_Hypervisor_Types

Task

• Type-1 vs Type-2

Output

Comparison Table

────────────────────────────────────────────

LAB 03

Day03_03_Resource_Allocation_Plan

Task

Create Resource Allocation Plan

64GB RAM
16 Core CPU

Output

Planning Document

────────────────────────────────────────────

LAB 04

Day03_04_Hypervisor_Comparison

Task

Compare

• VMware ESXi
• KVM

Output

Comparison Table
```

---

# 📖 Story Ending

> **NetMan_Khalid:**  
> "একটা Physical Server দিয়েই একাধিক Team-এর কাজ করা সম্ভব!"

> **Finance_Arif:**  
> "Resource Waste কমলো, Cost-ও কমলো!"

> **Security_Shahed:**  
> "Isolation ঠিক থাকলে Security-ও ঠিক থাকবে।"

> **DevOps_Taj:**  
> "Virtualization ছাড়া Enterprise Infrastructure কল্পনা করা যায় না!"

```text
🎉 THE END 🎉

Virtualization

✔ Better Resource Utilization

✔ Lower Cost

✔ Faster Provisioning

✔ Enterprise Ready
```

---

# ➡️ Next Episode

## **Episode 04 - AWS EC2**

> Learn how AWS EC2 uses Virtual Machines, Instance Types, AMIs, EBS, Security Groups, and Elastic IPs to run enterprise workloads in the cloud.