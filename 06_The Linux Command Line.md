# 🏦 Nord Bank - Episode 06: The Linux Command Line

**📖 তারিখ:** Saturday, 20 January, 10:00 AM  
**📍 স্থান:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The System Check

SA_Asraf NetMan_Khalid-এর ডেস্কে এলেন।

**SA_Asraf:**

> Khalid ভাই। Application Support Team বলছে—Internal Portal স্লো হয়ে যাচ্ছে। কী করব?

**NetMan_Khalid:**

> EC2 Instance-এ SSH করে Check করি।

**SA_Asraf:**

> SSH তো করি। কিন্তু তারপর কী দেখব?

**NetMan_Khalid:**

> Linux Commands দিয়ে Resource Check করতে হবে। CPU, RAM, Disk—সব Check করব।

**SA_Asraf:**

> GUI তো নেই। সব Command Line দিয়ে করতে হবে?

**NetMan_Khalid:**

> হ্যাঁ। Infrastructure Engineer-এর Daily কাজ। চলুন দেখি।

---

# 🏢 Scene 2: SSH Login

**SA_Asraf:**

> First step কী?

**NetMan_Khalid:**

> SSH Login।

### Steps Explained

1. Terminal Open
2. `.pem` file permission ঠিক করতে হবে
3. SSH command দিয়ে Public IP-তে Connect করতে হবে

**SA_Asraf:**

> Login হলে কী দেখব?

**NetMan_Khalid:**

> Ubuntu Prompt দেখাবে। তারপর Command দিতে পারবে।

SA_Asraf SSH করলেন। Prompt এলো।

### 🧪 LAB

**LAB: EC2_SSH_Login**

---

# 📂 Scene 3: Navigation Commands

**NetMan_Khalid:**

> First—কোথায় আছি সেটা দেখি।

### Commands Explained

```text
pwd      → বর্তমান Directory দেখায়
ls       → কী কী File/Folder আছে দেখায়
ls -ltr  → Detail সহ List দেখায়
cd       → Directory Change করে
cd ..    → এক ধাপ পেছনে যায়
```

**SA_Asraf:**

> এই Commands দিয়ে কী করব?

**NetMan_Khalid:**

> কোথায় আছি, কী আছে, কোথায় যাব—এই তিনটা জানতে হয়।

**SA_Asraf:**

> নতুন Directory কীভাবে বানাব?

**NetMan_Khalid:**

> mkdir command দিয়ে।

### 🧪 LAB

**LAB: Linux_Navigation_Commands**

---

# 📄 Scene 4: File Commands

**SA_Asraf:**

> File নিয়ে কাজ করতে চাই।

**NetMan_Khalid:**

> File Commands দেখি।

### Commands Explained

```text
touch   → নতুন খালি File তৈরি করে
mkdir   → নতুন Directory তৈরি করে
vi      → File Edit করার জন্য Editor
cat     → File Content দেখায়
rm      → File Delete করে
rm -r   → Directory Delete করে (সাবধান!)
```

**SA_Asraf:**

> vi কীভাবে কাজ করে?

**NetMan_Khalid:**

> vi Editor-এ `i` চাপলে Insert Mode-এ যাবে। `Esc` চাপলে বের হবে। `:wq` লিখে Save ও Exit করতে হবে।

**SA_Asraf:**

> Save না করে Exit কীভাবে করব?

**NetMan_Khalid:**

> `:q!` ব্যবহার করবে।

### 🧪 LAB

**LAB: Linux_File_Commands**

---

# 📊 Scene 5: Resource Monitoring

**NetMan_Khalid:**

> এখন Server Performance Check করি।

### Commands Explained

```text
free -h   → RAM Usage দেখায়
nproc     → CPU Core সংখ্যা দেখায়
df -h     → Disk Space দেখায়
top       → Real-time Resource Monitor
```

**SA_Asraf:**

> top কী?

**NetMan_Khalid:**

> এটা Live Dashboard। CPU, Memory, Process—সব দেখায়। `q` চাপলে Exit হয়।

**SA_Asraf:**

> Portal স্লো কেন—এগুলো দেখেই বোঝা যায়?

**NetMan_Khalid:**

> হ্যাঁ। CPU 100% হলে Process Issue। RAM Full হলে Memory Issue। Disk Full হলে Storage Issue।

### 🧪 LAB

**LAB: Linux_Resource_Monitoring**

---

# 🗣️ Scene 6: Diagnose The Problem

**SA_Asraf:**

> Portal স্লো—কী দেখব?

**NetMan_Khalid:**

> প্রথমে `top` চালাও। কোন Process বেশি CPU নিচ্ছে দেখি।

**SA_Asraf:**

> CPU Normal। তাহলে?

**NetMan_Khalid:**

> `free -h` দিয়ে RAM Check করি।

**SA_Asraf:**

> RAM 80% Used। এটা কি Problem?

**NetMan_Khalid:**

> হ্যাঁ। এটা Memory Issue হতে পারে। Process Restart অথবা Memory Increase করতে হবে।

**SA_Asraf:**

> Disk Check করব?

**NetMan_Khalid:**

> `df -h` দিয়ে।

**SA_Asraf:**

> Disk 90% Used। তাহলে?

**NetMan_Khalid:**

> Log File Cleanup করতে হবে অথবা Storage Increase করতে হবে।

---

# 📖 Scene 7: The Lesson

**SA_Asraf:**

> 

## Key Learnings

```text
═══════════════════════════════════════════════════════════════
KEY LEARNINGS
═══════════════════════════════════════════════════════════════

LINUX ARCHITECTURE:
User → Shell (Bash) → Kernel → Hardware

NAVIGATION:
pwd → কোথায় আছি
ls → কী আছে
cd → কোথায় যাব

FILES:
touch → File তৈরি
vi → File Edit
cat → File দেখি
rm → Delete (সাবধান!)

RESOURCE MONITORING:
free -h → RAM
nproc → CPU Core
df -h → Disk
top → Live Monitor

BEST PRACTICE:
Destructive Command (rm -r) চালানোর আগে
pwd + ls দিয়ে Verify করুন
```

**Infra_Babu:**

> Linux শিখছি। এটা Infrastructure-এর Foundation।

---

# 💡 The Impact Summary

```text
═══════════════════════════════════════════════════════════════
📊 BEFORE vs AFTER - LINUX SKILLS
═══════════════════════════════════════════════════════════════

BEFORE (No Linux):
├── Server Issue হলে কী করব বুঝতাম না
├── GUI-তে নির্ভর করতে হতো
└── Problem Diagnose করতে পারতাম না

AFTER (Linux Commands):
├── SSH করে Server-এ ঢুকতে পারি
├── CLI দিয়ে সব কাজ করতে পারি
└── Resource Issue Diagnose করতে পারি
```

---

# 🗣️ Interview Q&A

## Q1: Operating System কী?

**Answer:**

> Operating System হলো Hardware এবং Software-এর মধ্যে যোগাযোগ স্থাপনকারী মাধ্যম। Application সরাসরি Hardware-এর সাথে কথা বলতে পারে না। সব Request Operating System-এর মাধ্যমে Hardware-এ যায়।

---

## Q2: Linux Kernel-এর ৪টি প্রধান দায়িত্ব কী?

**Answer:**

- Device Management
- Memory Management
- Process Management
- System Calls Handling

---

## Q3: Linux কেন Enterprise-এ জনপ্রিয়?

**Answer:**

- Free এবং Open Source
- Secure
- Fast এবং Lightweight
- Ubuntu, CentOS, RHEL-এর মতো Enterprise Distribution রয়েছে

---

## Q4: Server Slow হলে কীভাবে Diagnose করবেন?

**Answer:**

1. `top` দিয়ে CPU ও Process Check করুন।
2. `free -h` দিয়ে RAM Check করুন।
3. `df -h` দিয়ে Disk Usage Check করুন।

---

## Q5: Production-এ `rm -r` চালানোর আগে কী করবেন?

**Answer:**

- `pwd` দিয়ে বর্তমান Directory Verify করুন।
- `ls` দিয়ে File/Folder Confirm করুন।
- Backup আছে কিনা নিশ্চিত করুন।
- Delete করার আগে পুনরায় যাচাই করুন।

---

# 🎯 Self-Introduction (Updated)

```text
1. "হ্যালো, আমি NetMan_Khalid। Infrastructure DevOps Engineer।"

2. "Linux Command Line-এ কাজ করি—Navigation, File এবং Resource Monitoring করি।"

3. "EC2 Instance-এ SSH করে Server Manage করি।"

4. "top, free, df Commands দিয়ে Performance Diagnose করি।"

5. "Production-এ Safety Follow করি। rm -r চালানোর আগে Verify করি।"
```

---

# 📌 5 Key Takeaways

```text
1. Linux Architecture:
   User → Shell → Kernel → Hardware

2. Navigation Commands:
   pwd, ls, cd

3. File Commands:
   touch, vi, cat, mkdir, rm

4. Resource Monitoring:
   free -h, nproc, df -h, top

5. Safety First:
   rm -r চালানোর আগে সবসময় Verify করুন।
```

---

# ✅ Completion Checklist

```text
□ SSH দিয়ে EC2-তে Login করতে পারি?

□ Navigation Commands (pwd, ls, cd) ব্যবহার করতে পারি?

□ File Commands (touch, vi, cat, mkdir, rm) ব্যবহার করতে পারি?

□ Resource Monitoring (free, nproc, df, top) ব্যবহার করতে পারি?

□ Operating System এবং Linux Kernel-এর কাজ ব্যাখ্যা করতে পারি?
```

---

# 🧪 LAB Scenario Summary

```text
═══════════════════════════════════════════════════════════════
📋 LAB SCENARIO SUMMARY
═══════════════════════════════════════════════════════════════

***LAB: EC2_SSH_Login***

***LAB: Linux_Navigation_Commands***

***LAB: Linux_File_Commands***

***LAB: Linux_Resource_Monitoring***
═══════════════════════════════════════════════════════════════
```

---

# 📖 গল্পের শেষ

**NetMan_Khalid:**

> Linux Commands শিখলাম। এখন Server Issue Diagnose করতে পারব।

**SA_Asraf:**

> আমি GUI ছাড়া কাজ শিখছি। CLI-তে Confidence আসছে।

**Infra_Babu:**

> Linux হলো Infrastructure-এর Foundation। এটা অবশ্যই জানতে হবে।

**NOC_Jahid:**

> Monitoring Commands গুলো দৈনন্দিন কাজে অনেক সাহায্য করবে।

**DevOps_Taj:**

> Next—File Permissions এবং User Management শিখব।

---

```text
🎉 THE END 🎉

Remember:
Linux CLI is the foundation of Infrastructure Management.
```