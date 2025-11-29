# 🛡️ SecureTheCloud Identity Academy — Volume 1

## **Lab 03 — SCIM Provisioning (Microsoft Entra → AWS IAM Identity Center)**
Zero Trust Identity Layer

---

<div align="center">
 
![Identity Banner](../diagrams/identity-banner.png)

🔗 **https://SecureTheCloud.dev**  
📺 **https://www.youtube.com/@SecureTheCloud-dev**

</div>

---

# 🎯 **Objective**

In this lab, you will:

- Configure SCIM Provisioning from Microsoft Entra ID → AWS IAM Identity Center

- Enable automatic:

- User creation

- Group creation

- User/group membership sync

- Deactivation

- Validate SCIM connection

- Sync Entra security groups into AWS Identity Center

- # Prepare for Lab 04 — Permission Sets Assignment

This is the core identity automation layer of Volume 1.

---

# 🧩 **Prerequisites**

### ✔ Lab 01 — AWS IAM Identity Center
### ✔ Lab 02 — Microsoft Entra Enterprise App (SAML Federation)
### ✔ AWS SSO URL (captured in Lab 01)
### ✔ SCIM Endpoint
### ✔ SCIM Access Token (generated from AWS IAM Identity Center)
### ✔ Entra ID Admin permissions
### ✔ At least one Entra Security Group created (e.g., AWS-Developers)

---

# 🚀 **Step 1 — Open the Enterprise App in Microsoft Entra**

1. Visit: https://entra.microsoft.com

2. Go to:
Identity → Applications → Enterprise Applications

3. Select the Enterprise App you created in Lab 02 (e.g., SecureTheCloud)

Expected:
You should land on the Enterprise App Overview page.

---

# 🚀 **Step 2 — Open the Provisioning Blade**

1. From the left menu:
Provisioning → Overview

2. Under Provisioning Mode, select:
### ✔ Automatic

This tells Entra:

“Entra will sync objects into AWS IAM Identity Center using SCIM.”

---

# 🚀 **Step 3 — Enter the SCIM Configuration**

From:
AWS IAM Identity Center → Settings → Identity Source

Copy the following into Entra:

### 🔹SCIM Endpoint

From AWS (example):

https://scim.<region>.amazonaws.com/scim/v2/

### 🔹SCIM Access Token

Paste exactly as generated from AWS.

# ⚠️ Never upload SCIM tokens to GitHub.

Paste into:
Provisioning → Admin Credentials

Click Test Connection.

Expected:
### ✔ Connection successful
### ✔ No errors

---

# 🚀 Step 4 — Start SCIM Provisioning

1. Click Save

2. Click Start Provisioning

Provisioning runs roughly every 40 minutes.

Entra will automatically sync:

- **Users**

- **Groups**

- **Group memberships**

---

# 🚀 Step 5 — Validate SCIM Synchronization in AWS

In AWS Console:
IAM Identity Center → Groups

You should see synced groups such as:

AWS-Developers

AWS-Admins

AWS-ReadOnly

Any additional Entra groups you created

These should now exist in AWS — with no manual creation required.

---

# 🧪 Lab Completion Checklist

### ✔ SCIM connection established
### ✔ Connection test successful
### ✔ Entra → AWS SCIM sync enabled
### ✔ Groups appear in AWS
### ✔ No manual IAM users
### ✔ Identity lifecycle now automated

---
# 🚀 Next Lab

➡️ Lab 04 — Permission Sets Assignment
04-permission-sets.md
---
⬅️ Back to Theory

📘 Chapter 04 — Federation Theory
../theory/04-federation-theory.md

📘 Chapter 06 — Permission Sets & RBAC
../theory/06-permission-sets-rbac.md
---
# 🔙 Back to Volume 1 README

https://github.com/S3curethecloud/multi-cloud-identity-aws-entra
---

# 🧭 SecureTheCloud Footer

<div align="center">

</div>



