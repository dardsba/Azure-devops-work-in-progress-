# AZ-500 Labs – Lab 01: Role-Based Access Control (Exercise 1)

A hands-on walk-through of **Exercise 1** from the official AZ‑500 “Role‑Based Access Control” lab. In this exercise you’ll create a test user and a **Senior Admins** security group in Microsoft Entra ID (formerly Azure AD) and add the user as both **member** and **owner**, using the **Azure portal**. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

> This repo will grow over time as additional exercises are added. For the full, canonical lab series, refer to Microsoft’s official AZ‑500 labs. [3](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies)

---

## Lab Scenario (condensed)

You’re preparing a proof of concept to demonstrate how **users** and **groups** are created and how **RBAC** ties roles to groups. In Exercise 1, you’ll focus on directory objects only: create a user **Joseph Price** and a **Senior Admins** group, then add Joseph to that group (and make him an owner). Later exercises assign Azure roles to groups. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

---

## Prerequisites

- **Azure permissions:** Sign in with an account that is **Owner or Contributor** in the subscription **and** **Global Administrator** in the Microsoft Entra tenant. These rights are required to create users and groups. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
- **Azure portal:** [https://portal.azure.com](https://portal.azure.comcom/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
- **Region note:** The official lab uses **East US** for its examples; confirm your region policy if you’re following the full lab set. (Region choice doesn’t impact Exercise 1 because it’s directory-only.) [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

---

## Exercise 1 — Create “Senior Admins” and add Joseph Price (Azure portal)

**Estimated time:** ~10 minutes. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

### Task 1 — Create a test user: *Joseph Price*

1. Open the **Azure portal** and in the global search, type **Microsoft Entra ID**; open your tenant. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
2. Go to **Users** ➜ **+ New user** ➜ ensure **Create user** is selected. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
3. Enter:
   - **User name (UPN):** `Joseph@<your_tenant_domain>`
   - **Name / Display name:** `Joseph Price`
   - Leave **Auto-generate password** enabled; **Show password** to copy it for later. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
4. Click **Create**, then refresh **Users | All users** and confirm **Joseph Price** appears. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

> ✅ **Result:** A new Entra ID user account for **Joseph Price** exists in your tenant. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

---

### Task 2 — Create the **Senior Admins** security group and add/own Joseph

1. In **Microsoft Entra ID**, open **Groups** ➜ **+ New group**. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
2. Configure:
   - **Group type:** `Security`
   - **Group name:** `Senior Admins`
   - **Membership type:** `Assigned` [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
3. Choose **Owners** ➜ **Add owners** ➜ select **Joseph Price** ➜ **Select**. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
4. Choose **Members** ➜ **Add members** ➜ select **Joseph Price** ➜ **Select**. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
5. Click **Create**. After creation, open the group and verify **Joseph** shows as **Owner** and **Member**. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

> ✅ **Result:** The **Senior Admins** group exists and includes **Joseph Price** as both **Owner** and **Member**—ready for RBAC role assignment in later exercises. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

---

## Verify Your Work

- **Users:** Microsoft Entra ID ➜ **Users** → confirm **Joseph Price** is listed. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
- **Groups:** Microsoft Entra ID ➜ **Groups** → open **Senior Admins** → check **Members** and **Owners** tabs for Joseph. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

---

## Troubleshooting Tips

- **Permission errors creating users/groups:** Ensure your signed-in account is **Global Administrator** for the tenant and **Owner/Contributor** at subscription scope. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
- **UPN domain issues:** If you have multiple verified domains, use the tenant’s default domain (e.g., `something.onmicrosoft.com`) for simplicity in labs. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
- **Can’t find Microsoft Entra ID?:** Use the top search bar in the Azure portal and type **Entra**; select **Microsoft Entra ID** from results. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

---

## What’s Next (preview)

- **Exercise 2:** Create **Junior Admins** with user **Isabel Garcia** using **PowerShell**.  
- **Exercise 3:** Create **Service Desk** with user **Dylan Williams** using **Azure CLI**.  
- **Exercise 4:** Assign **Virtual Machine Contributor** RBAC role to **Service Desk** at the appropriate scope. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)

---

## RBAC in One Minute (context)

Azure **RBAC** lets you assign granular permissions to **security principals** (users, groups, service principals) at scopes such as **subscription**, **resource group**, or **resource**. Group-based assignments simplify management—add users to groups; assign roles to groups. This lab uses that model. [2](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-500)

---

## References

- **Official lab instructions (Lab 01 – RBAC):** Microsoft Learning GitHub. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_01_RBAC.md)  
- **AZ-500 Study Guide** (skills measured, updates, resources): Microsoft Learn. [2](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-500)

---

## Repo Usage

This repo captures my step-by-step notes and artifacts for AZ‑500 labs. Feel free to fork and adapt to your own tenant setup.