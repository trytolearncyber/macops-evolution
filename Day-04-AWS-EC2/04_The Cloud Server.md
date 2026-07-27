# 🏦 Nord Bank - Episode 04: The Cloud Server

**📖 Date:** Thursday, 18 January, 10:00 AM  
**📍 Location:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Problem

**Infra_Babu** NetMan_Khalid-এর ডেস্কে এলেন।

> **Infra_Babu:**  
> Khalid ভাই! On-premise Data Center-এ আর জায়গা নেই! নতুন server রাখার মতো room নেই!

> **NetMan_Khalid:**  
> আমাদের তো অনেক server দরকার!

> **Infra_Babu:**  
> হ্যাঁ! কিন্তু Data Center full!

> **NetMan_Khalid:**  
> Cloud-এ যেতে হবে।

> **Infra_Babu:**  
> Cloud? মানে?

> **NetMan_Khalid:**  
> AWS। সেখানে Server ভাড়া নেওয়া যায়। Physical Server কেনার দরকার নেই।

---

# 🏢 Scene 2: The Meeting

> **NetMan_Khalid:**  
> Team! On-premise Data Center full। Cloud-এ যেতে হবে!

> **Finance_Arif:**  
> Multi-Cloud কেন না? AWS + Azure + GCP?

> **DevOps_Taj:**  
> Arif vai! Multi-Cloud জটিল। Single-Cloud (AWS) ভালো!

---

# Single-Cloud vs Multi-Cloud

| **Single-Cloud (AWS)** | **Multi-Cloud** |
|-------------------------|-----------------|
| Skill সহজ | Skill বেশি লাগে |
| Cost সহজ | Cost জটিল |
| Automation সহজ | Automation জটিল |
| Compliance সহজ | Compliance জটিল |

## Nord Bank Decision

✅ **Single-Cloud (AWS)**

---

> **SA_Asraf:**  
> AWS-তে Server কীভাবে কাজ করে?

> **NetMan_Khalid:**  
> AWS EC2 হচ্ছে Virtual Machine। Day 03-এর Virtualization-এর বাস্তব রূপ।

---

# 💡 Scene 3: What is EC2?

> **DevOps_Taj:**  
> EC2 = Elastic Compute Cloud। Request করলে AWS Virtual Machine (Instance) তৈরি করে দেয়।

---

# AWS EC2 Architecture

```text
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
  EC2  EC2  EC2
(Virtual Machines)
```

> **SA_Asraf:**  
> On-premise VMware-এর মতো?

> **NetMan_Khalid:**  
> Concept একই। শুধু Platform আলাদা।

---

# 🛠️ Scene 4: EC2 Creation Methods

> **Infra_Babu:**  
> EC2 Instance কীভাবে তৈরি করব?

> **DevOps_Taj:**  
> প্রধান ৩টি Method শিখলেই যথেষ্ট।

---

# EC2 Creation Methods

| Method | Use Case |
|---------|----------|
| Console | শেখার সময় |
| AWS CLI | Automation ও Scripting |
| Terraform ⭐ | Infrastructure as Code (Best Practice) |

**Recommended:** Terraform

---

> **Infra_Babu:**  
> Terraform কেন?

> **DevOps_Taj:**  
> Industry Standard, Multi-Cloud Support এবং বিশাল Community।

---

# 🖥️ Scene 5: First EC2 Instance (Console)

> **SA_Asraf:**  
> Console দিয়ে কীভাবে Instance তৈরি করি?

> **DevOps_Taj:**  
> AWS Console-এ গিয়ে **Launch Instance** ক্লিক করতে হবে।

---

## Instance Configuration

| Setting | Value |
|---------|-------|
| Name | nordbank-test-server |
| Operating System | Ubuntu 22.04 LTS |
| Instance Type | t2.micro |
| Key Pair | nordbank-test-key |

শেষে **Launch Instance** ক্লিক করুন।

---

> **SA_Asraf:**  
> মাত্র 10 মিনিটে Server Ready!

> **NetMan_Khalid:**  
> এটাই Cloud-এর Power।

---

# 🔑 Scene 6: Key Pair Explained

> **Security_Shahed:**  
> Key Pair কী?

> **NetMan_Khalid:**  
> SSH Login Credential।

---

# AWS Key Pair

| Public Key | Private Key |
|------------|-------------|
| AWS-এ সংরক্ষিত থাকে | `.pem` File হিসেবে Download করা হয় |

## Important

- `.pem` File কখনো Git Repository-তে Push করবেন না।
- Secure Folder-এ সংরক্ষণ করুন।
- হারিয়ে গেলে Instance-এ Login করা যাবে না।

---

> **Security_Shahed:**  
> Banking Sector-এ Key Management খুব গুরুত্বপূর্ণ।

---

# 📋 Scene 7: AWS Free Tier

> **Finance_Arif:**  
> এই Instance-এর Cost কত?

> **DevOps_Taj:**  
> Learning-এর জন্য Free Tier।

---

# AWS Free Tier

| Item | Value |
|------|-------|
| Instance | t2.micro |
| CPU | 1 vCPU |
| RAM | 1 GB |
| Storage | 30 GB EBS |
| Duration | 12 Months Free |

### Best For

- Learning
- Testing
- Development

---

> **Finance_Arif:**  
> Production-এও কি t2.micro?

> **NetMan_Khalid:**  
> না। Production-এর জন্য m5.large বা তার চেয়ে বড় Instance।

---

# ⚡ Scene 8: Public IP & Connectivity

> **NOC_Jahid:**  
> Instance তৈরি হলে Access কীভাবে করব?

> **DevOps_Taj:**  
> Public IP দিয়ে SSH করব।

> **NOC_Jahid:**  
> এটা কি Security Risk?

> **NetMan_Khalid:**  
> Security Group দিয়ে Control করা হয়। Day 12-এ বিস্তারিত।

---

# ✅ Scene 9: The Result

# On-Premise vs AWS EC2

| **On-Premise** | **AWS EC2** |
|----------------|-------------|
| 10–15 Days | 5 Minutes |
| Physical Hardware | No Hardware |
| Manual Configuration | Automated Configuration |
| High Cost | Pay-as-you-Go |

---

> **SA_Asraf:**  
> 5 মিনিটে Server! বিশ্বাসই হচ্ছে না!

---

# 🗣️ Interview Q&A

### Q: AWS EC2 কী?

**Answer:**

Virtual Machine Service। Day 03-এর Virtualization-এর বাস্তব রূপ।

---

### Q: EC2 Creation Methods কী?

**Answer:**

- Console
- AWS CLI
- Terraform

---

### Q: Single-Cloud কেন?

**Answer:**

- Skill সহজ
- Cost সহজ
- Automation সহজ
- Compliance সহজ

---

### Q: Key Pair কী?

**Answer:**

SSH Login Credential। `.pem` File নিরাপদে রাখতে হবে।

---

### Q: Production-এ Console দিয়ে EC2 তৈরি করবেন?

**Answer:**

না।

Terraform অথবা AWS CLI ব্যবহার করা হবে।

---

# 🎯 Self Introduction (MAC Matrix)

1. Hello, আমি **MAC Matrix**।
2. Infrastructure DevOps Engineer হিসেবে On-Premise এবং AWS Cloud নিয়ে কাজ করি।
3. EC2 Instance তৈরি করতে পারি Console, CLI এবং Terraform দিয়ে।
4. Single-Cloud (AWS) Strategy Follow করি।
5. Key Pair এবং Security Group নিরাপদভাবে পরিচালনা করি।

---

# 📌 Five Takeaways

1. EC2 = Virtual Machine
2. Free Tier = t2.micro
3. Key Pair = SSH Login Credential
4. EC2 Creation Methods = Console, CLI, Terraform
5. Nord Bank Strategy = Single-Cloud (AWS)

---

# 🛠️ Day 04 Tools

| Tool | Purpose |
|------|---------|
| AWS Management Console | EC2 Management |
| AWS EC2 | Virtual Machine Service |
| SSH Client (Terminal / PuTTY / MobaXterm) | Remote Login |
| `.pem` File | SSH Authentication |

---

## Required

- AWS Console
- SSH Client

> No additional software installation required.

---

# 📋 Day 04 Labs

## Day04_01_AWS_EC2_Concept

**Task**

AWS EC2 Concept এবং Single-Cloud vs Multi-Cloud বুঝতে হবে।

**Output**

EC2 Concept Summary

---

## Day04_02_EC2_Creation_Methods

**Task**

EC2 Instance তৈরির Method গুলো বুঝতে হবে।

**Output**

EC2 Creation Methods List

---

## Day04_03_Free_Tier_EC2_Creation

**Task**

Nord Bank Testing Team-এর জন্য একটি Free Tier EC2 Instance তৈরি করতে হবে।

**Output**

EC2 Instance Created (t2.micro)

---

## Day04_04_Key_Pair_Management

**Task**

EC2-এর জন্য Key Pair তৈরি করতে হবে এবং `.pem` File নিরাপদে সংরক্ষণ করতে হবে।

**Output**

- Key Pair Created
- SSH Login Successful

---

# 🎉 THE END

**📌 Previous:** Day 03 - Virtualization Fundamentals

**📌 Next:** Day 05 - AWS CLI & IAM