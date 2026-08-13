# IT-Support-Lab-Portfolio
Hands-on IT Support, Systems Administration, and Networking Lab Projects
---
## Phase 1: Network Diagnostics & Connectivity

In this phase, I diagnosed local network adapter settings, tested external IP reachability via ICMP, and verified DNS name resolution.

* **Checked Local IP & Adapter State:** `ip a` — Displays network interfaces, status, and assigned local IPv4/IPv6 addresses.
* **Tested Internet Reachability:** `ping -c 4 8.8.8.8` — Sends ICMP Echo Requests to Google's public DNS server to confirm outbound internet connectivity (bypassing DNS).
* **Tested DNS Resolution:** `ping -c 4 google.com` — Verifies that the system can translate human-readable domain names into machine-readable IP addresses.

![Local Interface Check](01_ip_a_network_check.png)

![ICMP and DNS Test](02_ping_dns_test.png)

## Phase 2: Role-Based Access Control & User Provisioning

### 3. Security Group & User Creation
Provisioned an departmental security group and added a new user account adhering to role-based access management.

* **Commands Executed:**
  * `sudo groupadd IT_Helpdesk` — Creates the secondary security group for IT personnel.
  * `sudo useradd -m -s /bin/bash jdoe` — Creates user account `jdoe`, generates a `/home` directory (`-m`), and sets the default shell to Bash (`-s /bin/bash`).
  * `sudo passwd jdoe` — Sets an initial password for authentication.
  * `sudo usermod -aG IT_Helpdesk jdoe` — Appends user `jdoe` to the `IT_Helpdesk` secondary group without overwriting existing memberships.
  * `id jdoe` — Validates user UID, default GID, and assigned group memberships.

![User and Group Onboarding](03_user_group_provisioning.png)

### 4. Shared Directory & Permission Hardening

Created a secure departmental directory and applied strict role-based access control.

Commands Executed:
* `sudo mkdir /opt/IT_Secure_Docs` — Creates the shared directory under /opt for departmental files.
* `sudo chown -R root:IT_Helpdesk /opt/IT_Secure_Docs` — Sets user ownership to root and group ownership to IT_Helpdesk recursively (-R).
* `sudo chmod -R 770 /opt/IT_Secure_Docs` — Applies "770" permissions (rwxrwx---), granting full access to root and IT_Helpdesk members while completely blocking all other system users.
* `ls -ld /opt/IT_Secure_Docs` — Displays long-format directory metadata to verify ownership, group assignment, and permissions.
