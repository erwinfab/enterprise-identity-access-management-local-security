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

  
* **IAM Compliance Enforcement**:

Provision user account dbadmin1 to inherit supplementary group privileges, enforce a forced password change on initialization, restrict password cycling frequency to a 10-day minimum floor, and apply a hard 30-day account expiration ceiling.
  
* **Privilege Escalation Routing**:

Grant standard superuser access to the admin account via explicit configuration inside the local sudoers engine.
  
* **Hardened Collaborative Workspace**:

Establish directory /home/dbadmin1/grading/review2 engineered with an active mask (umask 007) to block general read vectors, assign proper resource ownership, enforce strict Set Group ID (SGID) inheritance rules, and apply a data-deletion block (Sticky Bit).

## 🛠️ High-Level Deployment and Configuration Steps

**Step 1: Resource Optimization & Process Triage**


Query the active task manager subsystem to isolate the process ID execution vector exhibiting runaway CPU utilization metrics, and execute an immediate terminal command to reclaim host computational bandwidth.  

* Analyze runtime process execution hierarchies and isolate high-overhead PIDs
   * `top`
    
* Gracefully terminate or force-kill the rogue process entry
   * `kill <TARGET_PID>`

<img width="809" height="392" alt="image" src="https://github.com/user-attachments/assets/913fd860-8051-44ce-aeeb-017ff30732d4" />

<img width="809" height="357" alt="image" src="https://github.com/user-attachments/assets/e54ee9b0-8312-426a-be79-79f68524cf59" />

---

**Step 2: Enterprise Identity & Access Policy Enforcement**


Provision the organizational directory access groups and construct the primary administrator profile mapped against strict structural lifecycle compliance definitions.  

* Provision the corporate security group with explicit GID definitions
   * `groupadd -g 50000 database`

* Initialize the administrative user account with secondary group mapping
   * `useradd -G database dbadmin1`

* Establish initial account credential mapping
   * `passwd dbadmin1`

* Enforce a post-deployment forced password reset upon original authentication loop
   * `chage -d 0 dbadmin1`

* Apply strict structural lifecycle metrics (10-day minimum floor, 30-day rotation max)
   * `chage -m 10 -M 30 dbadmin1`

* Deploy explicit privilege escalation rules inside the sudoers layout mapping
   * `echo "dbadmin1 ALL=(ALL) ALL" > /etc/sudoers.d/dbadmin1`

<img width="691" height="366" alt="image" src="https://github.com/user-attachments/assets/022c8450-50ff-43b5-8ecc-e7c166762bd2" />

---

**Step 3: Hardened Shared Directory Architecture & Special Permissions**


Modify system environment default masks to intercept group permissions leakages and apply sticky indicators onto shared directory environments to preserve collaborative data integrity.  


* Establish environmental bit-mask controls inside the target profile config
   * `echo "umask 007" >> /home/dbadmin1/.bashrc`

* Provision the production collaborative node directory
   * `mkdir -p /home/dbadmin1/grading/review2`

* Execute an ownership overhaul across the targeted storage path directory
   * `chown dbadmin1:database /home/dbadmin1/grading/review2`

* Configure directory constraints:
   * Allow full read(4)/write(2)/execute(1) for the owner and group (7), allow read/execute for others (5), force Set Group ID (SGID) group ownership inheritance (2), and lock down unauthorized content deletions using the Sticky Bit (1)
   * `chmod 3775 /home/dbadmin1/grading/review2`

<img width="736" height="257" alt="image" src="https://github.com/user-attachments/assets/26e7f0c6-2d0f-4ef7-a442-7ff30cc41cdb" />

## 📊 Verification and Testing

**Step 1: System Security Policy Compliance Verification**


Execute the external automated testing mechanism to verify error-free deployment of identities, directory parameters, and privilege paths.

<img width="719" height="511" alt="image" src="https://github.com/user-attachments/assets/17c7f9a0-4c00-4403-bb4c-9c1bd4df984e" />

**Step 2: Sandbox Environment Teardown**


De-provision local sandbox elements to safely return the environment back to pre-test baseline states.  


<img width="702" height="289" alt="image" src="https://github.com/user-attachments/assets/a8043c83-8737-4fa4-99e6-40f8b36f1052" />
