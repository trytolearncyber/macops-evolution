# LAB: Day04_03_Free_Tier_EC2_Creation

**Task:** Nord Bank Testing Team-এর জন্য Free Tier EC2 Instance তৈরি করতে হবে।

---

# Free Tier EC2 Instance Creation

## Step 1: Open AWS Console

- Login to **AWS Management Console**
- Navigate to **EC2 Dashboard**

---

## Step 2: Launch Instance

Click **Launch Instance**

---

## Step 3: Configure Instance

| Setting | Value |
|---------|-------|
| Instance Name | `nordbank-test-server` |
| AMI | Ubuntu Server 22.04 LTS |
| Instance Type | t2.micro (Free Tier Eligible) |
| Key Pair | Create `nordbank-test-key` |
| Network Settings | Default |

---

## Step 4: Launch Instance

Click **Launch Instance**.

---

## Step 5: Verify Instance Status

Go to **EC2 → Instances**

Verify:

- Instance State = **Running** ✅
- Status Check = **2/2 Checks Passed**

---

## Step 6: Note the Public IP

Copy the assigned **Public IPv4 Address** for SSH access.

Example:

```text
13.127.xxx.xxx
```

---

# Instance Summary

| Item | Value |
|------|-------|
| Instance Name | nordbank-test-server |
| Instance Type | t2.micro (Free Tier) |
| CPU | 1 vCPU |
| RAM | 1 GB |
| Storage | 30 GB EBS |
| Key Pair | nordbank-test-key |
| Public IP | 13.127.xxx.xxx |
| Status | Running ✅ |

---

# Lab Result

- ✅ EC2 Instance Created
- ✅ Ubuntu 22.04 Installed
- ✅ Free Tier (t2.micro)
- ✅ Instance Running
- ✅ Public IP Assigned

---
---
---
---

# LAB: Day04_04_Key_Pair_Management

**Task:** EC2 Instance-এর জন্য Key Pair তৈরি করতে হবে এবং `.pem` File নিরাপদে সংরক্ষণ করতে হবে।

---

# Key Pair Management

## Step 1: Create Key Pair

Navigate to:

**AWS Console → EC2 → Key Pairs → Create Key Pair**

Configuration:

| Setting | Value |
|---------|-------|
| Name | nordbank-test-key |
| Key Type | RSA |
| Private Key Format | `.pem` |
| Download | Save Securely |

---

## Step 2: Set File Permission (Linux/macOS)

```bash
chmod 400 nordbank-test-key.pem
```

This command makes the private key readable only by the owner.

---

## Step 3: Connect Using SSH

```bash
ssh -i nordbank-test-key.pem ubuntu@<public-ip>
```

### Example

```bash
ssh -i nordbank-test-key.pem ubuntu@13.127.xxx.xxx
```

---

## Step 4: Verify Login

```bash
ubuntu@ip-xxx:~$ whoami
ubuntu

ubuntu@ip-xxx:~$ pwd
/home/ubuntu
```

Successful output confirms that SSH login is working.

---

## Step 5: Exit the Session

```bash
exit
```

---

# Security Best Practices

- Keep the `.pem` file in a secure location.
- Never upload the `.pem` file to GitHub or any public repository.
- Never share the private key with others.
- Create a backup in an encrypted location.
- If the key is lost, SSH access to the instance may no longer be possible without additional recovery steps.

---

# Lab Result

- ✅ Key Pair Created (`nordbank-test-key`)
- ✅ `.pem` File Downloaded
- ✅ File Permission Configured
- ✅ SSH Login Successful
- ✅ Session Exited Successfully