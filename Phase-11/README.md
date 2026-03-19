Phase 11: Data At-Rest Encryption (SSE with CMK)
Project Overview
In this phase, I transitioned the MediSecure infrastructure from standard platform-managed encryption to Customer-Managed Keys (CMK). This ensures that sensitive medical dispatcher data is secured by cryptographic keys managed within a private Azure Key Vault, meeting high-level regulatory compliance standards.

Technical Execution
Key Vault Hardening: Configured MediSecure-KV with Purge Protection and firewall exceptions for Trusted Microsoft Services.

Infrastructure Bridge: Provisioned a Disk Encryption Set (MediSecure-DiskSet) to link the Virtual Machine storage to the Key Vault.

Identity & Access (IAM): Granted the Disk Encryption Set the Key Vault Crypto Service Encryption User role to allow the secure exchange of cryptographic material.

VHD Encryption: Successfully updated the OS disk of the YYC-Dispatcher-VM to Server-Side Encryption with Customer-Managed Keys (SSE with CMK).

Troubleshooting & Resolution
The Challenge: Encountered initial deployment failures and "Unauthorized" errors due to Key Vault firewall restrictions and VM provisioning conflicts.

The Fix: Pivoted from legacy encryption methods to the Disk Encryption Set architecture. Temporarily whitelisted the administrator's Client IP to resolve permission handshakes and ensured the VM was in a deallocated state to clear the "Failed" provisioning loop.

Verification of Success
Validation: Verified the encryption status in the Azure Portal as SSE with CMK.

Evidence: Documented the successful update via Azure Resource Health and Notification logs.
### **Visual Evidence**

#### **1. Disk Encryption Set Infrastructure**
The "bridge" created to link the Key Vault and the VM.
![Disk Encryption Set](./image_b80386.png)

#### **2. Successful Deployment**
The Azure notification confirming the disk update was successful.
![Success Notification](./image_b71f42.png)

#### **3. Final Verification (SSE with CMK)**
Confirmed: The OS disk is now secured with Customer-Managed Keys.
![Final Status](./image_b71ea8.png)
