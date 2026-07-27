# ✅ Day 07 - Hands-On Labs Solved

---

# LAB: Day07_01_Linux_File_Permissions

**Task:** Nord Bank-এর Backup Script-এ সঠিক Permission Set করতে হবে। `777` Permission থেকে `750`-এ Change করতে হবে।

## ✅ Solution

### Linux File Permissions

### Step 1: Check Current Permission

```bash
ls -l nordbank-backup.sh
```

Output

```text
-rwxrwxrwx 1 ubuntu ubuntu 1024 Jan 22 10:00 nordbank-backup.sh
```

> `777` = Everyone has Read, Write and Execute permission.

---

### Step 2: Change Permission to 750

```bash
chmod 750 nordbank-backup.sh
```

---

### Step 3: Verify Permission

```bash
ls -l nordbank-backup.sh
```

Output

```text
-rwxr-x--- 1 ubuntu ubuntu 1024 Jan 22 10:00 nordbank-backup.sh
```

Meaning

| User | Permission |
|------|------------|
| Owner | rwx (7) |
| Group | r-x (5) |
| Others | --- (0) |

---

## Result

- ✅ Permission Changed from **777 → 750**
- ✅ Owner = Read, Write, Execute
- ✅ Group = Read, Execute
- ✅ Others = No Access

---

# LAB: Day07_02_Linux_User_Group_Management

**Task:** নতুন Infrastructure Team Member-এর জন্য User তৈরি করতে হবে এবং তাকে Infrastructure Team Group-এ যোগ করতে হবে।

## ✅ Solution

### User & Group Management

### Step 1: Create Group

```bash
sudo groupadd infra-team
```

Output

```text
(Group created successfully)
```

---

### Step 2: Create User

```bash
sudo adduser --disabled-password --gecos "" rahim-support
```

Output

```text
(User created successfully)
```

---

### Step 3: Add User to Group

```bash
sudo usermod -aG infra-team rahim-support
```

Output

```text
(User added successfully)
```

---

### Step 4: Verify Group Membership

```bash
groups rahim-support
```

Output

```text
rahim-support : rahim-support infra-team
```

---

### Step 5: Verify User Details

```bash
id rahim-support
```

Output

```text
uid=1002(rahim-support)
gid=1002(rahim-support)
groups=1002(rahim-support),1001(infra-team)
```

---

## Result

- ✅ Group Created (`infra-team`)
- ✅ User Created (`rahim-support`)
- ✅ User Added to Group
- ✅ Group Membership Verified

---

# LAB: Day07_03_Linux_Process_Management

**Task:** একটি Process বেশি Resource নিচ্ছে। Process Identify করতে হবে এবং Graceful Kill করতে হবে।

## ✅ Solution

### Process Management

### Step 1: View All Processes

```bash
ps aux
```

Output

```text
(Shows all running processes)
```

---

### Step 2: Search Specific Process

```bash
ps aux | grep sleep
```

Output

```text
ubuntu 12345 0.0 0.0 sleep 1000
```

---

### Step 3: Find Top CPU Processes

```bash
ps aux --sort=-%cpu | head -10
```

Output

```text
(Top 10 CPU consuming processes)
```

---

### Step 4: Gracefully Stop Process

```bash
kill 12345
```

Output

```text
(Process terminated successfully)
```

---

### Step 5: Verify Process

```bash
ps aux | grep sleep
```

Output

```text
(No matching process found)
```

---

### Step 6: Check Service Status

```bash
systemctl status ssh
```

Output

```text
Active: active (running)
```

---

### Step 7: Stop Service

```bash
sudo systemctl stop ssh
```

Output

```text
(Service stopped)
```

---

## Result

- ✅ Process List Viewed
- ✅ Process Identified
- ✅ Graceful Kill Completed
- ✅ Service Status Verified

---

# LAB: Day07_04_Linux_Cron_Jobs

**Task:** Backup Script প্রতিদিন রাত **2:00 AM**-এ Auto Run করার জন্য Cron Job তৈরি করতে হবে এবং Log File রাখতে হবে।

## ✅ Solution

### Cron Job Setup

### Step 1: Create Backup Script

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

### Step 2: Make Script Executable

```bash
chmod +x nordbank-backup.sh
```

---

### Step 3: Open Crontab

```bash
crontab -e
```

---

### Step 4: Add Cron Entry

```cron
0 2 * * * /home/ubuntu/nordbank-backup.sh
```

---

### Step 5: Verify Cron Job

```bash
crontab -l
```

Output

```text
0 2 * * * /home/ubuntu/nordbank-backup.sh
```

---

### Step 6: Verify Log File

```bash
cat /home/ubuntu/backup-log.txt
```

Output

```text
Backup started at Tue Jan 22 02:00:01 UTC 2026

Filesystem      Size Used Avail Use% Mounted on
/dev/root       29G  8.1G 20G   29% /
```

---

## Result

- ✅ Cron Job Created
- ✅ Backup Script Scheduled
- ✅ Log File Generated
- ✅ Daily Auto Execution Enabled

---

# LAB: Day07_05_Linux_Backup_Script_Cron

**Task:** Nord Bank-এর Backup Script সম্পূর্ণ Setup করতে হবে।

## ✅ Solution

### Complete Backup Script Setup

### Step 1: Create Script

```bash
touch nordbank-backup.sh
```

---

### Step 2: Add Script Content

```bash
vi nordbank-backup.sh
```

Content

```bash
#!/bin/bash

# Backup Script - Nord Bank
# Created: 22 Jan 2026

echo "=== Backup Log ===" >> /home/ubuntu/backup-log.txt
echo "Backup started at $(date)" >> /home/ubuntu/backup-log.txt
df -h >> /home/ubuntu/backup-log.txt
echo "Disk usage recorded" >> /home/ubuntu/backup-log.txt
echo "------------------------" >> /home/ubuntu/backup-log.txt
```

---

### Step 3: Set Permission

```bash
chmod 750 nordbank-backup.sh
```

---

### Step 4: Set Owner & Group

```bash
sudo chown ubuntu:infra-team nordbank-backup.sh
```

---

### Step 5: Verify Permission

```bash
ls -l nordbank-backup.sh
```

Output

```text
-rwxr-x--- 1 ubuntu infra-team 1024 Jan 22 10:00 nordbank-backup.sh
```

---

### Step 6: Add Cron Job

```bash
crontab -e
```

Add

```cron
0 2 * * * /home/ubuntu/nordbank-backup.sh
```

---

### Step 7: Verify Cron Job

```bash
crontab -l
```

Output

```text
0 2 * * * /home/ubuntu/nordbank-backup.sh
```

---

### Step 8: Test Script

```bash
./nordbank-backup.sh
```

Output

```text
(Script executed successfully)
```

---

### Step 9: Verify Log File

```bash
cat /home/ubuntu/backup-log.txt
```

Output

```text
=== Backup Log ===

Backup started at Tue Jan 22 10:05:01 UTC 2026

Filesystem      Size Used Avail Use% Mounted on
/dev/root       29G  8.1G 20G   29% /

Disk usage recorded
------------------------
```

---

## Result

- ✅ Script Created
- ✅ Permission Set (750)
- ✅ Owner Set (ubuntu:infra-team)
- ✅ Cron Job Added
- ✅ Script Tested Successfully
- ✅ Log File Generated

---

# ✅ Day 07 - All Labs Summary

| Lab | Status | Result |
|------|--------|--------|
| **Day07_01_Linux_File_Permissions** | ✅ | Permission Changed (777 → 750) |
| **Day07_02_Linux_User_Group_Management** | ✅ | User Created + Added to Group |
| **Day07_03_Linux_Process_Management** | ✅ | Process Identified + Graceful Kill |
| **Day07_04_Linux_Cron_Jobs** | ✅ | Cron Job Created + Log Generated |
| **Day07_05_Linux_Backup_Script_Cron** | ✅ | Complete Backup Script Setup |

---

# 🎉 ALL LABS SOLVED SUCCESSFULLY 🎉