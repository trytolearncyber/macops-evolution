# 🏦 Nord Bank - Episode 07: The Permission & Automation Challenge

**📖 Date:** Monday, 22 January, 9:30 AM  
**📍 Location:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Problem

**Compliance_Rassell** NetMan_Khalid-এর ডেস্কে এলেন। হাতে একটি Audit Report।

> **Compliance_Rassell:**  
> Khalid ভাই! Audit Report বলছে Backup Script-এর Permission `777`!

> **NetMan_Khalid:**  
> `777` মানে সবাই Read, Write, Execute করতে পারে। এটা Security Risk!

> **Compliance_Rassell:**  
> আরেকটা সমস্যা। Backup Script এখনও Manual Run করা হয়।

> **NetMan_Khalid:**  
> Automation দরকার। Cron Job দিয়ে Schedule করতে হবে।

---

# 🏢 Scene 2: The Meeting

> **NetMan_Khalid:**  
> Team! Backup Script-এ `777` Permission রাখা যাবে না। Manual Run-ও বন্ধ করতে হবে।

> **Security_Shahed:**  
> `777` মানে সবাই Full Access। Banking Sector-এ এটা গ্রহণযোগ্য নয়।

> **SA_Asraf:**  
> আমি সবাইকে Permission দিয়ে দিয়েছিলাম!

> **DevOps_Taj:**  
> Least Privilege Principle অনুসরণ করতে হবে। যতটুকু দরকার, ততটুকুই Permission।

---

# 💡 Scene 3: Linux File Permissions

> **DevOps_Taj:**  
> Linux Permission System বুঝে নেই।

---

# File Permission Basics

Example Output

```text
-rwxr-x--- 1 ubuntu infra-team 1024 Jan 22 10:00 script.sh
```

### Permission Breakdown

| Permission | Meaning |
|------------|---------|
| `rwx` | Owner: Read, Write, Execute |
| `r-x` | Group: Read, Execute |
| `---` | Others: No Permission |

---

## Numeric Values

| Permission | Value |
|------------|------:|
| Read (`r`) | 4 |
| Write (`w`) | 2 |
| Execute (`x`) | 1 |

Examples

| Permission | Numeric |
|------------|---------|
| rwx | 7 |
| r-x | 5 |
| --- | 0 |

---

## Common Permissions

| Permission | Description |
|------------|-------------|
| **750** | Owner Full, Group Read & Execute, Others No Access ✅ |
| **755** | Owner Full, Group Read & Execute, Others Read & Execute |
| **777** | Everyone Full Access ❌ Never Use |

---

> **Security_Shahed:**  
> Backup Script-এর জন্য `750` যথেষ্ট।

---

# 👥 Scene 4: User & Group Management

> **NetMan_Khalid:**  
> শুধু Infrastructure Team Script চালাতে পারবে।

---

# Group Management

## Create Group

```bash
sudo groupadd infra-team
```

---

## Create User

```bash
sudo adduser --disabled-password --gecos "" rahim-support
```

---

## Add User to Group

```bash
sudo usermod -aG infra-team rahim-support
```

---

## Verify Group Membership

```bash
groups rahim-support
```

Output

```text
rahim-support : rahim-support infra-team
```

---

> **Audit_Mahfuz:**  
> এখন Audit করা সহজ। কে কোন Group-এ আছে, সহজেই দেখা যায়।

---

# 🔧 Scene 5: Process Management

> **NOC_Jahid:**  
> কোন Process বেশি Resource নিচ্ছে কীভাবে দেখব?

---

# Process Management Commands

## View All Processes

```bash
ps aux
```

---

## Search a Process

```bash
ps aux | grep backup
```

---

## Gracefully Stop a Process

```bash
kill <PID>
```

---

## Force Stop a Process

```bash
kill -9 <PID>
```

---

## Manage Services

Check Service Status

```bash
systemctl status ssh
```

Start Service

```bash
systemctl start <service>
```

Stop Service

```bash
systemctl stop <service>
```

Restart Service

```bash
systemctl restart <service>
```

---

> **Security_Shahed:**  
> `kill -9` শেষ বিকল্প। আগে Graceful Kill ব্যবহার করুন।

---

# ⏰ Scene 6: Cron Job Automation

> **NetMan_Khalid:**  
> Backup Script Automatic চালাতে হবে।

---

# Cron Job Syntax

```text
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of Week (0-6)
│ │ │ └──── Month (1-12)
│ │ └────── Day of Month (1-31)
│ └──────── Hour (0-23)
└────────── Minute (0-59)
```

---

## Examples

Daily at **2:00 AM**

```text
0 2 * * *
```

Every **5 Minutes**

```text
*/5 * * * *
```

---

> **SA_Asraf:**  
> Cron Job-এর Log রাখা উচিত?

> **NetMan_Khalid:**  
> অবশ্যই।

```bash
>> /var/log/backup.log 2>&1
```

এতে Output এবং Error দুটোই Log File-এ সংরক্ষিত হবে।

---

# 📋 Scene 7: Backup Script Setup

> **DevOps_Taj:**  
> সম্পূর্ণ Setup দেখে নেওয়া যাক।

---

## Step 1: Create Script

```bash
touch nordbank-backup.sh
```

---

## Step 2: Edit Script

```bash
vi nordbank-backup.sh
```

Content

```bash
#!/bin/bash

echo "Backup started at $(date)" >> /home/ubuntu/backup-log.txt
df -h >> /home/ubuntu/backup-log.txt
```

---

## Step 3: Set Permission

```bash
chmod 750 nordbank-backup.sh
```

---

## Step 4: Set Owner

```bash
sudo chown ubuntu:infra-team nordbank-backup.sh
```

---

## Step 5: Schedule Cron Job

```bash
crontab -e
```

Add

```text
0 2 * * * /home/ubuntu/nordbank-backup.sh
```

---

## Step 6: Verify

View Cron Jobs

```bash
crontab -l
```

Check Log

```bash
cat /home/ubuntu/backup-log.txt
```

---

> **SA_Asraf:**  
> `750` মানে Owner Full Access, Group Read & Execute।

> **Security_Shahed:**  
> এখন Script Security Compliant।

---

# ✅ Scene 8: The Result

# Before vs After

| **Before** | **After** |
|------------|-----------|
| `777` Permission | `750` Permission ✅ |
| Manual Script Execution | Automated Cron Job ✅ |
| No User & Group Management | User & Group Control ✅ |
| Process Management জানা ছিল না | Process Management শিখেছি ✅ |

---

# 🗣️ Interview Q&A

### Q: `chmod 750` মানে কী?

**Answer**

- Owner = `7` (`rwx`)
- Group = `5` (`r-x`)
- Others = `0` (`---`)

---

### Q: Cron-এর ৫টি Field কী?

**Answer**

1. Minute
2. Hour
3. Day of Month
4. Month
5. Day of Week

---

### Q: `kill -9` কেন Avoid করবেন?

**Answer**

Force Kill করলে Data Corruption বা Incomplete Processing হতে পারে।

---

### Q: Cron Job-এ Log রাখা কেন জরুরি?

**Answer**

Script Error Troubleshooting এবং Debugging সহজ হয়।

---

### Q: `777` Permission কেন ব্যবহার করবেন না?

**Answer**

কারণ এতে সবাই Read, Write এবং Execute করতে পারে, যা বড় Security Risk।

---

# 🎯 Self Introduction (MAC Matrix)

1. Hello, আমি **MAC Matrix**।
2. Linux File Permission `chmod` এবং `chown` ব্যবহার করে Manage করি।
3. User এবং Group Management করি।
4. Cron Job ব্যবহার করে Automation তৈরি করি।
5. `ps`, `kill`, `systemctl` ব্যবহার করে Process এবং Service Manage করি।

---

# 📌 Five Takeaways

1. Linux Permission = `rwx` (`4`, `2`, `1`)
2. `750` হলো Production-এর জন্য নিরাপদ Permission
3. User + Group = Access Control
4. Cron = Task Automation
5. `777` Never Use, `kill -9` Last Option

---

# 🛠️ Day 07 Tools

| Tool | Purpose |
|------|---------|
| SSH Client | Remote Login |
| `.pem` File | EC2 Authentication |
| `chmod` | Change File Permission |
| `chown` | Change Owner & Group |
| `groupadd` | Create Group |
| `adduser` | Create User |
| `usermod` | Add User to Group |
| `ps` | View Running Processes |
| `kill` | Stop Process |
| `systemctl` | Manage Services |
| `crontab` | Schedule Automated Tasks |

---

## Required Tools

- SSH Client (Terminal / PuTTY / MobaXterm)
- EC2 Key Pair (`.pem`)
- Built-in Linux Administration Commands

> No additional software installation required.

---

# 📋 Hands-on Labs - Day 07

## Day07_01_Linux_File_Permissions

**Task**

Backup Script-এর `777` Permission পরিবর্তন করে `750` করতে হবে।

**Output**

Permission Changed to `750`

---

## Day07_02_Linux_User_Group_Management

**Task**

নতুন Infrastructure Team Member-এর জন্য User তৈরি করতে হবে এবং `infra-team` Group-এ যোগ করতে হবে।

**Output**

User Created + Added to Group

---

## Day07_03_Linux_Process_Management

**Task**

Running Process খুঁজে বের করতে হবে এবং Graceful Kill করতে হবে।

**Output**

Process Identified + Graceful Kill Completed

---

## Day07_04_Linux_Cron_Jobs

**Task**

Backup Script প্রতিদিন রাত **2:00 AM**-এ Auto Run করার জন্য Cron Job তৈরি করতে হবে এবং Log File সংরক্ষণ করতে হবে।

**Output**

Cron Job Created + Log File Generated

---

## Day07_05_Linux_Backup_Script_Cron

**Task**

Backup Script Create, Permission Set, Owner Set এবং Cron Job Configure করতে হবে।

**Output**

Complete Backup Script Setup Completed

---

# 🎉 THE END

**📌 Previous:** Day 06 - Linux Command Line Basics

**📌 Next:** Day 08 - Bash Scripting – Part 1