# LAB: Day03_02_Hypervisor_Types

**Task:** Type-1 vs Type-2 Hypervisor পার্থক্য বুঝতে হবে।

---

# Type-1 vs Type-2 Hypervisor Comparison

| **Type-1 (Bare-Metal)** | **Type-2 (Hosted)** |
|--------------------------|---------------------|
| সরাসরি Hardware-এর উপর চলে | Existing OS-এর উপরে চলে (Windows, macOS, Linux) |
| কোনো Operating System দরকার নেই | Operating System দরকার |
| Performance ভালো | Performance তুলনামূলক কম |
| Enterprise Environment-এ ব্যবহার করা হয় | Testing ও Learning-এর জন্য বেশি ব্যবহার হয় |
| **Examples:** VMware ESXi, KVM | **Examples:** VirtualBox, VMware Workstation |

---

## Nord Bank Use Case

| Environment | Hypervisor |
|------------|------------|
| Production | VMware ESXi (Type-1) |
| Testing | VirtualBox (Type-2) |

---
---
---



# LAB: Day03_03_Resource_Allocation_Plan

**Task:** Nord Bank-এর 64GB RAM, 16 Core Server-এর জন্য Resource Allocation Plan তৈরি করতে হবে।

---

# Resource Allocation Plan - Nord Bank

## Physical Server

| Component | Specification |
|-----------|---------------|
| Server Model | Dell PowerEdge R750 |
| RAM | 64 GB |
| CPU | 16 Core |

---

## Team Requirements

| Team | RAM | CPU |
|------|-----|-----|
| Application Support | 8 GB | 4 Core |
| DevOps Team | 8 GB | 4 Core |
| SOC Team | 16 GB | 4 Core |
| NOC Team | 8 GB | 2 Core |

---

## Resource Calculation

| Item | RAM | CPU |
|------|-----|-----|
| Total Required | 40 GB | 14 Core |
| Total Available | 64 GB | 16 Core |
| Buffer | 24 GB | 2 Core |
| Buffer Percentage | 37.5% | 12.5% |

---

## VM Allocation Plan

| VM Name | RAM | CPU |
|---------|-----|-----|
| app-support-vm | 8 GB | 4 Core |
| devops-vm | 8 GB | 4 Core |
| soc-vm | 16 GB | 4 Core |
| noc-vm | 8 GB | 2 Core |

---

## Hypervisor

**VMware ESXi (Enterprise Standard)**

---

## Benefits

- Resource Utilization: **60–70%**
- Cost Saving: **40–50%**
- Buffer Available: **37.5%** (Unexpected Load Handle)
- Strong VM Isolation with **VMware ESXi**

---
---
---





# LAB: Day03_04_Hypervisor_Comparison

**Task:** VMware ESXi এবং KVM Hypervisor তুলনা করতে হবে।

---

# Hypervisor Comparison: VMware ESXi vs KVM

| **VMware ESXi** | **KVM** |
|-----------------|---------|
| **Vendor:** VMware (Broadcom) | **Vendor:** Open-source (Linux Kernel, Red Hat, Canonical) |
| **Cost:** Paid (License Required) | **Cost:** Free (Open Source) |
| **Type:** Type-1 (Bare-Metal) | **Type:** Type-1 (Bare-Metal) |
| **Use Case:** Enterprise Data Center, Banking | **Use Case:** Cloud Providers (OpenStack), Cost-sensitive Enterprise |
| **Features:** vMotion, HA, DRS (Advanced) | **Features:** Live Migration (Basic) |
| **Performance:** Excellent | **Performance:** Very Good |
| **Support:** Enterprise Support | **Support:** Community Support |

---

# Nord Bank Recommendation

✅ **Recommended Hypervisor:** **VMware ESXi**

### Why VMware ESXi?

- Enterprise Features (vMotion, HA, DRS)
- Strong Isolation and Security
- Banking Industry Standard
- Enterprise-grade Vendor Support