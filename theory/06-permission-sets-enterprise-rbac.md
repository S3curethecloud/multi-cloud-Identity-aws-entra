# 🧩 SecureTheCloud Academy — Volume 1  
## **Chapter 06 — Permission Sets & Enterprise RBAC**

---

<div align="center">

![Identity Banner](../diagrams/identity-banner.png)

📺 **Watch the RBAC & Permission Sets Lesson:**  
https://www.youtube.com/@SecureTheCloud-dev

</div>

---

# 🌍 Overview

Permission Sets are the **authorization layer** in AWS IAM Identity Center.

In an identity-federated environment:

- Entra ID = Authentication  
- SCIM = Provisioning  
- Permission Sets = Authorization  

This chapter teaches enterprise-grade RBAC for multi-cloud Zero Trust environments.

---

# 🧩 What Are Permission Sets?

AWS Permission Sets define:

- Allowed actions  
- Role session duration  
- Inline policies  
- AWS managed or custom policies  
- MFA requirements  
- Policy boundaries  

### Permission Sets become IAM Roles  
(with temporary credentials) assigned to users/groups.

---

# 🔐 Enterprise RBAC Strategy (Best Practices)

### 1️⃣ Role-Based Access  
Define roles based on **job function**, not individuals.

Examples:

- `Admin-Cloud-Security`  
- `Ops-Compute-Engineer`  
- `ReadOnly-Finance-Audit`  

### 2️⃣ Group → Permission Set → AWS Account  
The correct architecture is:

