# 🏦 Nord Bank - Episode 05: The Access Control Challenge

**📖 তারিখ:** Friday, 19 January, 9:00 AM  
**📍 স্থান:** Nord Bank Headquarters, Dhaka

---

# 🌅 Scene 1: The Security Concern

Security_Shahed দ্রুত NetMan_Khalid-এর ডেস্কে এলেন। হাতে একটি Report।

**Security_Shahed:**  
"Khalid ভাই। আমি Audit Report দেখছি। বলছে—আমাদের AWS Access Management ঝুঁকিপূর্ণ।"

**NetMan_Khalid:**  
"কী সমস্যা?"

**Security_Shahed:**  
"আমরা Root User Access Key use করছি। Programming Team-কে দেওয়া হয়েছে। কিন্তু Root User-এর Unlimited Access! Banking sector-এ এটা acceptable না।"

**NetMan_Khalid:**  
"ঠিক ধরেছেন। Root User দিয়ে daily কাজ করা যায় না। IAM User তৈরি করতে হবে।"

**Security_Shahed:**  
"আরেকটা সমস্যা—EC2 Instance-এ কীভাবে access করছি? Security Group ঠিক আছে তো?"

**NetMan_Khalid:**  
"SSH দিয়ে access করছি। Key Pair use করে। Security Group Port 22 open আছে।"

**Security_Shahed:**  
"Port 22 open? Public IP দিয়ে direct SSH?"

**NetMan_Khalid:**  
"হ্যাঁ। Production-এ direct SSH করা উচিত না। কিন্তু learning environment-এ temporary allowed।"

**Security_Shahed:**  
"Production-এর জন্য policy বানাতে হবে। কিন্তু আজকে IAM Setup করে ফেলি।"

NetMan_Khalid দ্রুত মিটিং ডাকলেন।

---

# 🏢 Scene 2: The Meeting

Meeting room-এ উপস্থিত:

- NetMan_Khalid (Infrastructure DevOps)
- Security_Shahed (Security Specialist)
- DevOps_Taj (DevOps Engineer)
- SA_Asraf (System Administrator)
- NOC_Jahid (NOC Lead)
- Compliance_Rassell (Compliance Lead)
- Audit_Mahfuz (Audit Lead)

**NetMan_Khalid:**

> Team। Security_Shahed বলছে—আমাদের AWS Access Management ঠিক করতে হবে। Root User Access Key use করা বন্ধ করতে হবে।

**SA_Asraf:**

> Root User কী? আমি তো AWS Console-এ login করি।

**DevOps_Taj:**

> Asraf vai। Root User হলো Account Creation-এর time-এর Master Account। Unlimited Access থাকে। Production-এ এটা use করা যায় না।

**NetMan_Khalid:**

> আমরা IAM User তৈরি করব। প্রতিটা Engineer-এর আলাদা User থাকবে।

**Compliance_Rassell:**

> ঠিক বলেছেন। Banking sector-এ accountability দরকার। কে কী করল—সেটা track করতে হয়।

**Audit_Mahfuz:**

> IAM User থাকলে audit easy। Root User দিয়ে কাজ করলে tracking hard।

**NetMan_Khalid:**

> চলুন শুরু করি।

---

# 💡 Scene 3: IAM Explained

**DevOps_Taj:**

> IAM = Identity and Access Management। এটা AWS-এর Security Service।

## IAM - 4 Main Concepts

```text
═══════════════════════════════════════════════════════════════
IAM - 4 MAIN CONCEPTS
═══════════════════════════════════════════════════════════════

1. ROOT USER
├── Account Creation-এর time-এর Master Account
├── Unlimited Access
└── শুধু Billing ও Account Setup-এর জন্য (Daily কাজে নয়)

2. IAM USER
├── নির্দিষ্ট Person-এর জন্য Identity
├── Limited Permission (Least Privilege)
└── উদাহরণ: rahim-devops, karim-devops

3. IAM GROUP
├── একাধিক User-কে একসাথে Permission দেওয়া
└── উদাহরণ: NordBank-DevOps-Team

4. IAM POLICY
├── JSON Document - কী কী Permission আছে
└── উদাহরণ: EC2 Read-Only, S3 Full Access

5. IAM ROLE
├── Service/Application-এর জন্য Temporary Permission
├── Hardcoded Key লাগে না
└── উদাহরণ: EC2 → S3 Read Permission
```

**Security_Shahed:**

> Root User-এর Access Key use করা সবচেয়ে বড় risk।

## Root User vs IAM User

```text
═══════════════════════════════════════════════════════════════
ROOT USER vs IAM USER
═══════════════════════════════════════════════════════════════

❌ ROOT USER ACCESS KEY:
├── Full, Unlimited AWS Access
├── Accountability নেই
└── মারাত্মক Security Risk

✅ IAM USER:
├── Limited Permission (Least Privilege)
├── Auditable (কে কী করল Tracking)
└── Nord Bank Standard
```

**SA_Asraf:**

> আমাদের কী করা দরকার?

**NetMan_Khalid:**

> IAM User তৈরি করতে হবে। CLI configure করতে হবে।

### 🧪 LAB

**LAB: IAM_User_Creation**

---

# 🖥️ Scene 4: Access Key Generation

**DevOps_Taj:**

> IAM User তৈরি করার পর Access Key generate করতে হবে।

**Security_Shahed:**

> Secret Access Key কখনো Share করবেন না। এটা Password-এর মতো।

**SA_Asraf:**

> Access Key দিয়ে কী করা যায়?

**NetMan_Khalid:**

> CLI দিয়ে AWS-তে কাজ করতে লাগে। Programmatic Access-এর জন্য।

### 🧪 LAB

**LAB: IAM_Access_Key_Generation**

---

# 🔑 Scene 5: CLI Setup

**DevOps_Taj:**

> এখন AWS CLI Configure করি। Terminal থেকে command দিতে হবে।

**SA_Asraf:**

> Configure হলে কী হয়?

**DevOps_Taj:**

> Credentials Store হয়। পরবর্তী command-এ authentication auto হয়।

**NOC_Jahid:**

> CLI install করা লাগে?

**NetMan_Khalid:**

> হ্যাঁ। Local Machine-এ AWS CLI install করতে হবে।

### 🧪 LAB

**LAB: AWS_CLI_Setup**

---

# 🗣️ Scene 6: Identity Verification

**NetMan_Khalid:**

> কে Login করছি—সেটা Verify করি।

**DevOps_Taj:**

> Command দিলে ARN দেখাবে। `user/nordbank-junior-engineer` দেখাচ্ছে। অর্থাৎ IAM User দিয়ে login করেছি। Root User নয়।

**Audit_Mahfuz:**

> Perfect। Audit trail maintain হবে।

**Security_Shahed:**

> Root User Access Key আর use করব না।

### 🧪 LAB

**LAB: AWS_CLI_Identity_Verify**

---

# 🧪 Scene 7: Permission Test

**NetMan_Khalid:**

> ReadOnly Policy কাজ করছে কিনা Test করি।

**DevOps_Taj:**

> Instance List দেখতে পাচ্ছি। কিন্তু তৈরি করতে পারব না। AccessDenied Error আসবে।

**Security_Shahed:**

> এইটাই Least Privilege-এর কাজ। যতটুকু দরকার ততটুকুই permission।

**Compliance_Rassell:**

> Banking sector-এ এটা mandatory।

### 🧪 LAB

**LAB: IAM_Permission_Test**

---

# 🔧 Scene 8: SSH Connection

**SA_Asraf:**

> EC2 Instance-এ SSH করতে চাই। কী করব?

**DevOps_Taj:**

> Terminal থেকে SSH command দিতে হবে। `.pem` file use করে।

**NOC_Jahid:**

> Public IP দিয়ে direct SSH? Security risk?

**Security_Shahed:**

> Learning environment-এ temporary allowed। Production-এ VPN বা Bastion Host use করতে হবে।

**SA_Asraf:**

> SSH থেকে কীভাবে বের হব?

**DevOps_Taj:**

> `exit` command দিলে বের হবে।

### 🧪 LAB

**LAB: EC2_SSH_Login**

---

# 📖 Scene 9: The Lesson

**SA_Asraf:**

> আমি 15 years on-premise-এ কাজ করেছি। IAM প্রথম শিখলাম।

## Key Learnings

```text
═══════════════════════════════════════════════════════════════
KEY LEARNINGS
═══════════════════════════════════════════════════════════════

IAM = Who, What করতে পারবে—সেটা Control করে

ROOT USER:
├── Unlimited Access
├── শুধু Account Setup-এর জন্য
└── Daily কাজে ব্যবহার করবেন না

IAM USER:
├── Limited Permission
├── Auditable
└── Daily কাজের জন্য

LEAST PRIVILEGE:
├── যতটুকু দরকার—ততটুকুই Permission
├── ReadOnly দিয়ে Start করুন
└── প্রয়োজন অনুযায়ী বাড়ান

ACCESS KEY:
├── Programmatic Access-এর জন্য
├── Secret Access Key কখনো Share করবেন না
└── 90 দিন পর Rotate করুন
```

**Infra_Babu:**

> আমি IAM শিখছি। আগে জানতাম না।

**Security_Shahed:**

> এখন Security Improved।

---

# 💡 The Impact Summary

```text
═══════════════════════════════════════════════════════════════
📊 BEFORE vs AFTER - IAM
═══════════════════════════════════════════════════════════════

BEFORE (Root User):
├── Unlimited Access
├── Security Risk
├── Audit Hard
└── Accountability নেই

AFTER (IAM User):
├── Limited Access
├── Security Improved
├── Audit Easy
└── Accountability আছে
```

---

# 🗣️ Interview Q&A

### Q1: IAM কী? Root User আর IAM User-এর পার্থক্য কী?

**Answer:**

> IAM হলো AWS-এর Security Service। কে কী করতে পারবে সেটা Control করে। Root User হলো Master Account যার Unlimited Access থাকে। IAM User হলো নির্দিষ্ট Person-এর Identity যার Limited Permission দেওয়া যায়। Production-এ Root User ব্যবহার না করে IAM User ব্যবহার করা উচিত।

---

### Q2: IAM Role আর IAM User-এর মধ্যে পার্থক্য কী?

**Answer:**

> IAM User নির্দিষ্ট Person-এর জন্য এবং তার নিজস্ব Credential থাকে। IAM Role Service বা Application-এর জন্য Temporary Credential দেয়। Hardcoded Key লাগে না। উদাহরণ: EC2 Instance-কে S3 Access দেওয়া।

---

### Q3: Principle of Least Privilege কী?

**Answer:**

> প্রতিটি User বা Service-কে ঠিক যতটুকু Permission প্রয়োজন ততটুকুই দেওয়া। এর বেশি নয়। Banking Sector-এ এটি Security ও Compliance-এর জন্য অত্যন্ত গুরুত্বপূর্ণ।

---

### Q4: Access Key Leak হলে কী করবেন?

**Answer:**

1. Access Key Deactivate/Delete করুন।
2. নতুন Access Key Generate করুন।
3. CloudTrail Log Review করুন।
4. Root Password Change করুন।
5. MFA Enable করুন।

---

### Q5: Production-এ SSH Access কীভাবে Manage করবেন?

**Answer:**

- Public IP দিয়ে Direct SSH নয়।
- VPN অথবা Bastion Host ব্যবহার করুন।
- Security Group Restrict করুন।
- Key Pair Secure রাখুন।
- MFA Enable করুন।

---

# 🎯 Self-Introduction (Updated)

```text
1. "হ্যালো, আমি NetMan_Khalid। Infrastructure DevOps Engineer।"

2. "IAM User তৈরি করি—Least Privilege নীতি follow করি।"

3. "Root User Access Key ব্যবহার করি না। IAM User ব্যবহার করি।"

4. "SSH দিয়ে EC2 Instance access করি।"

5. "AWS CLI Configure করি। Access Key নিরাপদভাবে manage করি।"
```

---

# 📌 5 Key Takeaways

```text
1. IAM = Identity + Access Management

2. Root User = Unlimited Access

3. IAM User = Limited & Auditable Access

4. Least Privilege = যতটুকু দরকার ততটুকুই Permission

5. Secret Access Key কখনো Share করবেন না
```

---

# ✅ Completion Checklist

```text
□ SSH দিয়ে EC2-তে Login করতে পারি?

□ IAM User তৈরি করতে পারি?

□ AWS CLI Configure করতে পারি?

□ IAM User, Group, Policy, Role-এর পার্থক্য বলতে পারি?

□ Root User Access Key কেন এড়িয়ে চলতে হবে?
```

---

# 🧪 LAB Scenario Summary

```text
═══════════════════════════════════════════════════════════════
📋 LAB SCENARIO SUMMARY
═══════════════════════════════════════════════════════════════

***LAB: EC2_SSH_Login***

***LAB: IAM_User_Creation***

***LAB: IAM_Access_Key_Generation***

***LAB: AWS_CLI_Setup***

***LAB: AWS_CLI_Identity_Verify***

***LAB: IAM_Permission_Test***
═══════════════════════════════════════════════════════════════
```

---

# 📖 গল্পের শেষ

**NetMan_Khalid:**

> IAM Setup complete। Root User আর use করব না।

**Security_Shahed:**

> Security improved। Banking sector standard maintain করছি।

**Audit_Mahfuz:**

> Audit ready। IAM User tracking possible।

**SA_Asraf:**

> আমি IAM শিখলাম। Root User risk বুঝলাম।

**DevOps_Taj:**

> Next—Linux Administration শিখব।

---

```text
🎉 THE END 🎉

Remember:
IAM is the foundation of AWS Security.
```