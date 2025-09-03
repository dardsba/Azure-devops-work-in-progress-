# Lab 05: Securing Azure SQL Database

This exercise focuses on implementing security features for **Azure SQL Database**, including **Advanced Data Protection**, **Data Classification**, and **Auditing**.  
**Customizations applied:**  
- Changed **region** from East US to `polandcentral` for resource availability.  
- Adjusted **VM size** for any supporting infrastructure deployed via template.

---

## Lab Scenario (condensed)

You’ve been asked to review and implement security features for an Azure SQL Database to protect against threats like **SQL injection** and **data exfiltration**, classify sensitive data, and enable auditing for compliance. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_05_SecuringAzureSQLDatabase.MD)

---

## Tasks Overview

### Task 1 — Deploy Azure SQL Database
- Use the provided ARM template (`azuredeploy.json`) to deploy:
  - **SQL Server** and **SQL Database** (e.g., `AZ500LabDb`).
- Adjust **region** and **VM size** in the template as needed for your environment.  
- Validate deployment in the Azure portal. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_05_SecuringAzureSQLDatabase.MD)

---

### Task 2 — Configure Advanced Data Protection
- Enable **Microsoft Defender for SQL** on the SQL Server resource.
- Review **Vulnerability Assessment** and **Advanced Threat Protection** settings.
- Check **Recommendations** and **Security alerts** in Microsoft Defender for Cloud. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_05_SecuringAzureSQLDatabase.MD)

---

### Task 3 — Configure Data Classification
- Navigate to **SQL Database → Data Discovery & Classification**.
- Apply recommended sensitivity labels to columns (e.g., Confidential, Personal).
- Save changes and verify updated classification overview. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_05_SecuringAzureSQLDatabase.MD)

---

### Task 4 — Configure Auditing
- Enable **Server-level auditing**:
  - Set retention (e.g., 5 days).
  - Store logs in a new **Storage Account**.
- Enable **Database-level auditing** (optional; server-level applies by default).
- Validate by running queries in **Query Editor** and reviewing **Audit Logs**. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_05_SecuringAzureSQLDatabase.MD)

---

## Custom Fixes & Notes
- **Region Change:** Used `polandcentral` instead of East US.
- **VM Size Adjustment:** Modified template parameters for supporting resources.
- Verified deployment and security settings after changes.

---

## Verification Checklist
- SQL Database deployed and accessible.
- **Microsoft Defender for SQL** enabled.
- Data classification applied and visible in the portal.
- Auditing enabled and logs stored in the configured storage account.
- Audit logs show login attempts and query executions. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_05_SecuringAzureSQLDatabase.MD)

---

## References
- Official Lab Instructions