# 🏦 Nord Bank - Episode 06: The Linux Command Line

**📖 Date:** Saturday, 20 January, 10:00 AM  
**📍 Location:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Problem

**SA_Asraf** NetMan_Khalid-এর ডেস্কে এলেন।

> **SA_Asraf:**  
> Khalid ভাই! Application Support Team বলছে Internal Portal স্লো হয়ে যাচ্ছে!

> **NetMan_Khalid:**  
> EC2 Instance-এ SSH করে Check করি!

> **SA_Asraf:**  
> SSH তো করি। কিন্তু তারপর কী দেখব?

> **NetMan_Khalid:**  
> Linux Commands দিয়ে CPU, RAM, Disk Check করতে হবে!

> **SA_Asraf:**  
> GUI তো নেই! সব Command Line দিয়েই করতে হবে?

> **NetMan_Khalid:**  
> হ্যাঁ। Infrastructure Engineer-এর Daily কাজ।

---

# 🏢 Scene 2: SSH Login

> **SA_Asraf:**  
> First Step কী?

> **NetMan_Khalid:**  
> SSH Login।

---

# SSH Login

```bash
ssh -i nordbank-test-key.pem ubuntu@<public-ip>
```

### Example

```bash
ssh -i nordbank-test-key.pem ubuntu@13.127.xxx.xxx
```

### Result

```text
ubuntu@ip-xxx:~$
```

✅ Login Successful

---

# 📂 Scene 3: Navigation Commands

> **NetMan_Khalid:**  
> প্রথমে দেখি আমরা কোথায় আছি।

---

# Linux Navigation Commands

| Command | Purpose |
|---------|---------|
| `pwd` | বর্তমান Directory দেখায় |
| `ls` | File ও Folder List দেখায় |
| `ls -ltr` | Detail সহ List দেখায় |
| `cd` | Directory Change করে |
| `cd ..` | এক ধাপ পিছনে যায় |
| `cd ~` | Home Directory-তে ফিরে যায় |

---

## Example

```bash
ubuntu@ip-xxx:~$ pwd
/home/ubuntu

ubuntu@ip-xxx:~$ ls
nordbank-resource-report.sh

ubuntu@ip-xxx:~$ cd /tmp

ubuntu@ip-xxx:/tmp$ pwd
/tmp
```

> **SA_Asraf:**  
> কোথায় আছি, কী আছে, কোথায় যাব, এই তিনটা জানা দরকার।

---

# 📄 Scene 4: File Commands

> **SA_Asraf:**  
> File নিয়ে কাজ করতে চাই।

---

# Linux File Management Commands

| Command | Purpose |
|---------|---------|
| `touch` | নতুন File তৈরি করে |
| `mkdir` | নতুন Directory তৈরি করে |
| `vi` | File Edit করে |
| `cat` | File Content দেখায় |
| `rm` | File Delete করে |
| `rm -r` | Directory Delete করে |

---

## Example

```bash
touch test-file.txt

mkdir nordbank-lab

ls
```

Output

```text
test-file.txt
nordbank-lab
```

---

### Edit File

```bash
vi config-notes.txt
```

Useful Keys

| Key | Action |
|-----|--------|
| `i` | Insert Mode |
| `Esc` | Exit Insert Mode |
| `:wq` | Save & Exit |
| `:q!` | Exit Without Saving |

---

### Read File

```bash
cat config-notes.txt
```

Output

```text
Nord Bank Infra DevOps Lab - Day 06
```

---

### Delete File & Directory

```bash
rm test-file.txt

rm -r nordbank-lab
```

> **NetMan_Khalid:**  
> `rm -r` ব্যবহার করার আগে সবসময় Verify করবে।

---

# 📊 Scene 5: Resource Monitoring

> **NetMan_Khalid:**  
> এখন Server Performance Check করি।

---

# Linux Resource Monitoring Commands

| Command | Purpose |
|---------|---------|
| `free -h` | RAM Usage |
| `nproc` | CPU Core Count |
| `df -h` | Disk Usage |
| `top` | Real-time CPU, Memory & Process Monitor |

---

## Check Memory

```bash
free -h
```

Example

```text
              total        used        free      shared  buff/cache   available
Mem:           985Mi       312Mi        98Mi       1.0Mi       574Mi       521Mi
```

---

## Check CPU Cores

```bash
nproc
```

Output

```text
1
```

---

## Check Disk Usage

```bash
df -h
```

Example

```text
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        29G  8.1G   20G  29% /
```

---

## Live Resource Monitor

```bash
top
```

Features

- CPU Usage
- Memory Usage
- Running Processes
- System Load

Press **q** to exit.

---

# 🗣️ Scene 6: Diagnose the Problem

> **SA_Asraf:**  
> Portal Slow। কী দেখব?

> **NetMan_Khalid:**  
> প্রথমে `top` চালাও।

> **SA_Asraf:**  
> CPU Usage Normal।

> **NetMan_Khalid:**  
> এবার `free -h` দিয়ে RAM Check করো।

> **SA_Asraf:**  
> RAM 80% Used।

> **NetMan_Khalid:**  
> Memory Issue হতে পারে। Application Process Restart করতে হবে।

> **SA_Asraf:**  
> Disk Check করব?

> **NetMan_Khalid:**  
> `df -h`

> **SA_Asraf:**  
> Disk 90% Used।

> **NetMan_Khalid:**  
> পুরনো Log File Cleanup করতে হবে।

---

# ✅ Scene 7: The Result

# Before vs After

| **Before** | **After** |
|------------|-----------|
| Server Issue বুঝতাম না | SSH করে Server Access করতে পারি |
| GUI-এর উপর নির্ভর করতাম | CLI দিয়ে কাজ করতে পারি |
| Problem Diagnose করতে পারতাম না | Resource Issue Diagnose করতে পারি ✅ |

---

> **SA_Asraf:**  
> Linux Commands শিখে এখন Server Diagnose করতে পারব।

---

# 🗣️ Interview Q&A

### Q: Operating System কী?

**Answer**

Hardware এবং Software-এর মধ্যে Bridge হিসেবে কাজ করে।

---

### Q: Linux Kernel-এর কাজ কী?

**Answer**

- Process Management
- Memory Management
- Device Management
- Hardware Communication

---

### Q: Linux কেন জনপ্রিয়?

**Answer**

- Free
- Secure
- Fast
- Stable

---

### Q: Server Slow হলে কোন Command ব্যবহার করবেন?

**Answer**

```bash
top
free -h
df -h
```

---

### Q: `rm -r` চালানোর আগে কী করবেন?

**Answer**

```bash
pwd
ls
```

বর্তমান Directory Verify করবেন।

---

# 🎯 Self Introduction (MAC Matrix)

1. Hello, আমি **MAC Matrix**।
2. Linux Command Line ব্যবহার করে Server Manage করি।
3. Navigation, File Management এবং Resource Monitoring জানি।
4. `top`, `free`, `df` ব্যবহার করে Performance Diagnose করি।
5. Production Environment-এ Safety First Approach অনুসরণ করি।

---

# 📌 Five Takeaways

1. Linux Architecture = User → Shell → Kernel → Hardware
2. Navigation Commands = `pwd`, `ls`, `cd`
3. File Commands = `touch`, `vi`, `cat`, `mkdir`, `rm`
4. Resource Monitoring = `free`, `nproc`, `df`, `top`
5. `rm -r` ব্যবহারের আগে অবশ্যই Directory Verify করুন।

---

# 🛠️ Day 06 Tools

| Tool | Purpose |
|------|---------|
| SSH Client | EC2 Remote Login |
| `.pem` File | SSH Authentication |
| Linux Commands | Navigation, File Management, Resource Monitoring |

---

## Required Tools

- SSH Client (Terminal, PuTTY, MobaXterm)
- EC2 Key Pair (`.pem`)
- Built-in Linux Commands

> No additional software installation required.

---

# 📋 Hands-on Labs - Day 06

## Day06_01_Linux_Navigation

**Task**

`pwd`, `ls`, `cd` ব্যবহার করে Directory Explore করতে হবে।

**Output**

Navigation Commands Practice Completed

---

## Day06_02_Linux_File_Management

**Task**

`touch`, `vi`, `cat`, `mkdir`, `rm` ব্যবহার করে File এবং Folder Manage করতে হবে।

**Output**

File Management Commands Practice Completed

---

## Day06_03_Linux_Resource_Monitoring

**Task**

`free -h`, `nproc`, `df -h`, `top` ব্যবহার করে Server Resource Check করতে হবে।

**Output**

Resource Monitoring Practice Completed

---

## Day06_04_SSH_EC2_Access

**Task**

EC2 Instance-এ SSH Login করে Linux Commands Practice করতে হবে এবং Session Exit করতে হবে।

**Output**

SSH Login + Linux Commands Practice Completed

---

# 🎉 THE END

**📌 Previous:** Day 05 - AWS CLI & IAM

**📌 Next:** Day 07 - Linux Administration – Part 2