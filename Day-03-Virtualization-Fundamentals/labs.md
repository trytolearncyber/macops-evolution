# Day03_01_Resource_Allocation_Plan

## Objective

Create a resource allocation plan for Nord Bank's physical server and distribute resources among different teams using VMware ESXi.

---

# Resource Allocation Plan - Nord Bank

## Physical Server

| Component | Specification |
|-----------|---------------|
| Server Model | Dell PowerEdge R750 |
| RAM | 64 GB |
| CPU | 16 Cores |

---

## Team Resource Requirements

| Team | RAM | CPU |
|------|-----:|----:|
| Application Support | 8 GB | 4 Cores |
| DevOps Team | 8 GB | 4 Cores |
| SOC Team | 16 GB | 4 Cores |
| NOC Team | 8 GB | 2 Cores |

---

## Resource Calculation

| Item | RAM | CPU |
|------|-----:|----:|
| Total Required | 40 GB | 14 Cores |
| Total Available | 64 GB | 16 Cores |
| Buffer | 24 GB | 2 Cores |
| Buffer Percentage | 37.5% | 12.5% |

---

## VM Allocation Plan

| VM Name | RAM | CPU |
|---------|-----:|----:|
| `app-support-vm` | 8 GB | 4 Cores |
| `devops-vm` | 8 GB | 4 Cores |
| `soc-vm` | 16 GB | 4 Cores |
| `noc-vm` | 8 GB | 2 Cores |

---

## Hypervisor

**VMware ESXi (Enterprise Standard)**

---

## Benefits

- Resource Utilization: **60% - 70%**
- Cost Saving: **40% - 50%**
- Buffer Capacity: **37.5%** for unexpected workload
- Strong VM isolation using VMware ESXi

---

## Result

- ✅ Resource Allocation Plan Created
- ✅ 4 Virtual Machines Allocated
- ✅ 37.5% Resource Buffer Maintained
- ✅ VMware ESXi Recommended

---

# Day03_01_VMware_Workstation_Setup

## Objective

Create a test Ubuntu Server virtual machine using VMware Workstation.

---

# VMware Workstation - VM Creation

## Step 1

Open **VMware Workstation**.

---

## Step 2

Click **Create a New Virtual Machine**.

---

## Step 3

Select:

> **Typical (Recommended)**

Click **Next**.

---

## Step 4

Choose:

> **Installer disc image file (ISO)**

Browse and select the Ubuntu Server ISO file.

Click **Next**.

---

## Step 5

Configure the operating system.

| Setting | Value |
|---------|-------|
| Guest OS | Linux |
| Version | Ubuntu 64-bit |

Click **Next**.

---

## Step 6

Configure VM information.

| Setting | Value |
|---------|-------|
| VM Name | `nordbank-test-vm` |
| Location | Choose desired folder |

Click **Next**.

---

## Step 7

Configure virtual disk.

| Setting | Value |
|---------|-------|
| Disk Size | 20 GB |
| Storage Type | Store virtual disk as a single file |

Click **Next**.

---

## Step 8

Customize VM hardware.

| Resource | Value |
|----------|------:|
| RAM | 2048 MB (2 GB) |
| CPU | 2 Cores |

Click **Close** → **Finish**.

---

## Step 9

Start the virtual machine and install Ubuntu Server.

---

## Step 10

After installation:

- Log in to the server.
- Verify the VM status.

---

# Commands to Run Inside the VM

```bash
whoami
```

### Output

```text
ubuntu
```

---

```bash
free -h
```

### Sample Output

```text
              total        used        free      shared  buff/cache   available
Mem:           1.9Gi       312Mi        98Mi       1.0Mi       574Mi       521Mi
```

---

# VM Configuration Summary

| Item | Value |
|------|-------|
| VM Name | `nordbank-test-vm` |
| Operating System | Ubuntu Server |
| Status | Running |
| RAM | 2048 MB (2 GB) |
| CPU | 2 Cores |
| Disk | 20 GB |

---

# Result

- ✅ Virtual Machine Created
- ✅ Ubuntu Server Installed Successfully
- ✅ VM Running Successfully
- ✅ Configuration Verified
```