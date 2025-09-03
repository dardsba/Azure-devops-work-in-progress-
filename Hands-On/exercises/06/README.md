# Lab 06: Securing Azure Storage

This exercise demonstrates how to secure **Azure Storage accounts** using features like **Shared Access Signatures (SAS)**, **Azure AD-based access**, and **Storage Firewalls**.  
**Customizations applied:**  
- Changed **region** from East US to `polandcentral` for resource availability.  
- Adjusted **VM size** for supporting infrastructure to reduce cost.

---

## Lab Scenario (condensed)

You need to configure secure access to an Azure Storage account by:
- Creating a storage account and container.
- Uploading and accessing blobs securely.
- Implementing **SAS tokens** and **Azure AD authentication**.
- Restricting access using **network rules** and **firewalls**.

---

## Tasks Overview

### Task 1 — Deploy Storage Account
- Create a **Storage Account** in `polandcenrtal` with default redundancy (LRS).
- Enable **Secure transfer required**.
- Configure **Blob public access** as disabled.

---

### Task 2 — Create Container and Upload Blob
- Create a container (e.g., `images`) with **private access**.
- Upload a sample file (e.g., `sample.txt`).

---

### Task 3 — Configure Shared Access Signature (SAS)
- Generate a **SAS token** for read-only access.
- Test access using the SAS URL in a browser or `curl`.

---

### Task 4 — Enable Azure AD Authentication
- Assign **Storage Blob Data Reader** role to a user or VM-managed identity.
- Test access using Azure CLI or PowerShell with `az storage blob list`.

---

### Task 5 — Configure Storage Firewall and Network Rules
- Restrict access to **selected networks** or **specific IP ranges**.
- Validate that unauthorized IPs cannot access the storage account.

---

## Custom Fixes & Notes
- **Region Change:** Used `polancentral` instead of East US.
- **VM Size Adjustment:** Selected a smaller VM size for cost efficiency.
- Verified connectivity and access after applying firewall rules.

---

## Verification Checklist
- Storage account created with **secure transfer** enabled.
- Blob container and file uploaded successfully.
- SAS token works for allowed operations only.
- Azure AD-based access tested successfully.
- Firewall rules block unauthorized access.

---

## References
