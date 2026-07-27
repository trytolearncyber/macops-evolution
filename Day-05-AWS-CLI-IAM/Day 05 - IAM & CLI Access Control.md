# LAB: Day05_01_IAM_User_Creation

**Task:** নতুন Junior DevOps Engineer-এর জন্য IAM User তৈরি করতে হবে। `AmazonEC2ReadOnlyAccess` Policy Attach করতে হবে এবং Access Key Generate করতে হবে।

---

# IAM User Creation

## Step 1: Open IAM Console

Navigate to:

**AWS Console → IAM → Users → Create User**

---

## Step 2: Create User

Enter the following username:

```text
nordbank-junior-engineer
```

Click **Next**.

---

## Step 3: Attach Policy

Attach the AWS Managed Policy:

```text
AmazonEC2ReadOnlyAccess
```

This policy allows the user to **view EC2 resources** but prevents creating, modifying, or deleting them.

---

## Step 4: Create User

Click **Create User**.

---

## Step 5: Generate Access Key

Navigate to:

**IAM User → Security Credentials → Create Access Key**

Select:

```text
Use Case: Command Line Interface (CLI)
```

Download or securely copy:

- Access Key ID
- Secret Access Key

> **Important:** The Secret Access Key is shown only once. Store it securely.

---

# IAM User Summary

| Item | Value |
|------|-------|
| Username | nordbank-junior-engineer |
| Policy | AmazonEC2ReadOnlyAccess |
| Access Key ID | AKIAXXXXXXXXXXXXXXXX |
| Secret Access Key | xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx |

---

# Lab Result

- ✅ IAM User Created
- ✅ ReadOnly Policy Attached
- ✅ Access Key Generated
- ✅ Secret Access Key Stored Securely

---

# LAB: Day05_02_AWS_CLI_Setup

**Task:** Local Machine-এ AWS CLI Configure করতে হবে। IAM User-এর Access Key দিয়ে Authenticate করতে হবে এবং Identity Verify করতে হবে।

---

# AWS CLI Setup

## Step 1: Open Terminal

Launch Terminal, PowerShell, or Command Prompt.

---

## Step 2: Configure AWS CLI

Run:

```bash
aws configure
```

Enter the requested values.

```text
AWS Access Key ID:
AKIAXXXXXXXXXXXXXXXX

AWS Secret Access Key:
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Default Region Name:
ap-south-1

Default Output Format:
json
```

---

## Step 3: Verify Identity

Run:

```bash
aws sts get-caller-identity
```

Example Output

```json
{
  "UserId": "AIDA...",
  "Account": "123456789012",
  "Arn": "arn:aws:iam::123456789012:user/nordbank-junior-engineer"
}
```

The ARN confirms that the AWS CLI is authenticated using the IAM User.

---

# Lab Result

- ✅ AWS CLI Configured Successfully
- ✅ IAM User Authenticated
- ✅ Identity Verified

---

# LAB: Day05_03_IAM_Permission_Test

**Task:** ReadOnly Policy Test করতে হবে। EC2 Create করার চেষ্টা করলে `AccessDenied` আসতে হবে।

---

# IAM Permission Test

## Test 1: Read Permission

Run:

```bash
aws ec2 describe-instances
```

### Result

```text
Success
```

The EC2 instance list is displayed.

---

## Test 2: Write Permission

Run:

```bash
aws ec2 run-instances \
--image-id ami-0c55b159cbfafe1f0 \
--instance-type t2.micro \
--key-name test-key
```

### Result

```text
AccessDenied
```

Example Error

```text
An error occurred (AccessDenied) when calling the RunInstances operation:

User:
arn:aws:iam::123456789012:user/nordbank-junior-engineer

is not authorized to perform:

ec2:RunInstances
```

This confirms that the **Least Privilege Principle** is working correctly.

---

# Lab Result

- ✅ Read Permission Works
- ❌ Write Permission Denied
- ✅ Least Privilege Verified

---

# LAB: Day05_04_SSH_EC2_Access

**Task:** EC2 Instance-এ SSH Login করতে হবে এবং Session Exit করতে হবে।

---

# SSH EC2 Access

## Step 1: Get the Public IP

Navigate to:

**EC2 Dashboard → Instances → nordbank-test-server**

Copy the **Public IPv4 Address**.

---

## Step 2: Set File Permission

Linux/macOS:

```bash
chmod 400 nordbank-test-key.pem
```

---

## Step 3: Connect via SSH

Run:

```bash
ssh -i nordbank-test-key.pem ubuntu@<public-ip>
```

Example

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

ubuntu@ip-xxx:~$ ls
```

Successful output confirms that the SSH session is active.

---

## Step 5: Exit Session

```bash
exit
```

---

# Lab Result

- ✅ SSH Connection Successful
- ✅ Login Verified (`ubuntu`)
- ✅ Session Exited Successfully

---

# ✅ Day 05 - All Labs Summary

| Lab | Status | Result |
|-----|--------|--------|
| Day05_01_IAM_User_Creation | ✅ Completed | IAM User Created + Access Key Generated |
| Day05_02_AWS_CLI_Setup | ✅ Completed | AWS CLI Configured + Identity Verified |
| Day05_03_IAM_Permission_Test | ✅ Completed | Read Works ✅ + Create Fails ❌ |
| Day05_04_SSH_EC2_Access | ✅ Completed | SSH Login Successful |

---

# 🎉 Day 05 Completed Successfully

## Skills Learned

- IAM User Creation
- AWS Managed Policies
- AWS CLI Configuration
- Identity Verification using STS
- Least Privilege Principle
- EC2 Permission Testing
- Secure SSH Access to EC2
- AWS Security Best Practices

**🎉 ALL HANDS-ON LABS COMPLETED SUCCESSFULLY**