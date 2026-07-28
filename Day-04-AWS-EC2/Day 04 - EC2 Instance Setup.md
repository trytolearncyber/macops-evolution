# ✅ Day 04 - Hands-On Labs Solved

---

# LAB 01: Day04_01_Free_Tier_EC2_Creation

**Task:** Create a Free Tier EC2 Instance for the Nord Bank Testing Team.

---

## ✅ Solution

### Free Tier EC2 Instance Creation

### Step 1
Open **AWS Console** → **EC2 Dashboard**

### Step 2
Click **Launch Instance**

### Step 3
Set the instance name:

```text
nordbank-test-server
```

### Step 4
Select the AMI:

```text
Ubuntu Server 22.04 LTS
```

### Step 5
Choose the instance type:

```text
t2.micro (AWS Free Tier Eligible)
```

### Step 6
Create a new Key Pair:

```text
Name: nordbank-test-key
```

### Step 7
Keep the default network settings.

### Step 8
Click **Launch Instance**.

### Step 9
Wait until the instance status becomes:

```text
Running
```

### Step 10
Note the assigned Public IP address.

---

## Result

| Item | Value |
|------|-------|
| Instance Name | nordbank-test-server |
| Instance Type | t2.micro (Free Tier) |
| CPU | 1 vCPU |
| RAM | 1 GB |
| Storage | 30 GB EBS |
| Key Pair | nordbank-test-key |
| Public IP | 13.127.xxx.xxx |
| Status | ✅ Running |

---

## Commands to Verify

### Check Current User

```bash
whoami
```

Output

```text
ubuntu
```

### Check Kernel Information

```bash
uname -a
```

Output

```text
Linux ip-xxx 5.15.0-1022-aws #25-Ubuntu SMP
```

---

## Final Result

- ✅ EC2 Instance Created
- ✅ Instance Name: `nordbank-test-server`
- ✅ Instance Type: `t2.micro`
- ✅ Status: Running
- ✅ Public IP Assigned

---

# LAB 02: Day04_02_Key_Pair_Management

**Task:** Create an EC2 Key Pair and securely manage the `.pem` file.

---

## ✅ Solution

### Step 1: Create Key Pair

AWS Console

```text
EC2
 └── Key Pairs
      └── Create Key Pair
```

Configuration

| Setting | Value |
|---------|-------|
| Name | nordbank-test-key |
| Type | RSA |
| Format | .pem |

Download the `.pem` file and store it securely.

---

### Step 2: Set File Permission

```bash
chmod 400 nordbank-test-key.pem
```

**Why?**

To secure the private key so that SSH accepts it.

---

### Step 3: Connect Using SSH

```bash
ssh -i nordbank-test-key.pem ubuntu@<public-ip>
```

Example

```bash
ssh -i nordbank-test-key.pem ubuntu@13.127.xxx.xxx
```

---

### Step 4: Verify Login

Check the current user.

```bash
whoami
```

Output

```text
ubuntu
```

Check the current directory.

```bash
pwd
```

Output

```text
/home/ubuntu
```

List files.

```bash
ls
```

Output

```text
(Displays available files)
```

---

### Step 5: Exit SSH Session

```bash
exit
```

---

## Result

- ✅ Key Pair Created: `nordbank-test-key`
- ✅ `.pem` File Downloaded
- ✅ Permission Set to `400`
- ✅ SSH Login Successful
- ✅ Session Closed Successfully

---

## Security Tips

- Never upload the `.pem` file to GitHub.
- Store the private key in a secure location.
- If the `.pem` file is lost, direct SSH access to the instance is no longer possible.

---

# ✅ Day 04 - All Labs Summary

| Lab | Status |
|------|--------|
| Day04_01_Free_Tier_EC2_Creation | ✅ Completed |
| Day04_02_Key_Pair_Management | ✅ Completed |

---

## 🎉 Day 04 Completed Successfully

### Completed Labs

- ✅ Created an AWS Free Tier EC2 Instance
- ✅ Created and Managed an EC2 Key Pair
- ✅ Connected to the EC2 Instance Using SSH
- ✅ Verified Instance Status and Login
- ✅ Learned Basic EC2 Security Best Practices

---
**Status:** ✅ Day 04 Successfully Completed