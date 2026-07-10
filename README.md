# Red Hat Enterprise Linux (RHEL 9.3) Core Competency: Enterprise Identity, Access Management & Local Security

## 🎯Project Overview
This project validates administrative competencies in automated resource optimization, local Identity & Access Management (IAM), and advanced POSIX file system security controls within Red Hat Enterprise Linux 9.3. The objective is to secure an enterprise node by diagnosing and terminating rogue processes, provisioning privileged administrative accounts under rigid lifecycle constraints, and deploying a hardened multi-user collaboration directory utilizing inheritance permissions and deletion barriers.

## 💻Environments and Technologies Used
* **Operating System Environment**: Red Hat Enterprise Linux 9.3 (RHEL) 
* **Core Utilities Demanded**: `top`/`kill`, `groupadd`, `useradd`, `chage`, `chmod`/`chown`, Linux Access Control Lists (ACLs/Special Permissions)

## 📋Objectives and Scenario
The deployment scenario simulates standard production security hardening mandates to protect system resources and enforce data privacy boundaries across corporate directory environments.  

### Technical Specification Requirements:
* **Resource Optimization**: Isolate and terminate the highest CPU-consuming runaway process thread.
  
* **Group Provisioning**: Establish a dedicated security group named database bound to GID 50000.
  
* **IAM Compliance Enforcement**: Provision user account dbadmin1 to inherit supplementary group privileges, enforce a forced password change on initialization, restrict password cycling frequency to a 10-day minimum floor, and apply a hard 30-day account expiration ceiling.
  
* **Privilege Escalation Routing**: Grant standard superuser access to the admin account via explicit configuration inside the local sudoers engine.
  
* **Hardened Collaborative Workspace**: Establish directory /home/dbadmin1/grading/review2 engineered with an active mask (umask 007) to block general read vectors, assign proper resource ownership, enforce strict Set Group ID (SGID) inheritance rules, and apply a data-deletion block (Sticky Bit).

## 🛠️ High-Level Deployment and Configuration Steps

**Step 1:  **





## 📊 Verification and Testing
