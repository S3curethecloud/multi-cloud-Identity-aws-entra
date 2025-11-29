# 🧩 SecureTheCloud Academy — Volume 1  
## **Chapter 02 — AWS IAM Identity Center Overview**

---

<div align="center">

![Identity Banner](../diagrams/identity-banner.png)

📺 **Watch the AWS Identity Center Lesson:**  
https://www.youtube.com/@SecureTheCloud-dev

</div>

---

# 🌍 Overview

AWS IAM Identity Center (formerly AWS SSO) is the **central identity authority** for accessing AWS:

- AWS Console  
- AWS CLI  
- AWS SDK  
- AWS MFA sessions  
- AWS permission boundaries  

When integrated with Microsoft Entra ID, Identity Center becomes a **federated SP** (Service Provider) receiving tokens from Entra ID.

---

# 🔐 What Identity Center Controls

### ✔ Who can log in  
### ✔ Which AWS accounts they can access  
### ✔ What roles they receive  
### ✔ How temporary permissions are granted  
### ✔ How sessions are established  
### ✔ MFA enforcement (when not delegated to IdP)  

Identity Center = the authorization brain inside AWS.

---

# 🧩 Identity Center Constructs

### **1. Users & Groups**
- **Not local** if SCIM is enabled  
- Managed in Entra ID  
- Provisioned automatically to AWS  

### **2. Permission Sets**
Define:
- Allowed actions  
- Session duration  
- Policy boundaries  
- AWS managed or custom policies  

### **3. Assignments**
Glue between:
- User/Group  
- AWS Account  
- Permission Set  

### **4. Identity Source**
For federation:
- External Identity Provider = **Microsoft Entra ID**

---

# 🧠 How Identity Center Works with Entra ID

1. User signs into AWS → redirected to Entra ID  
2. Entra ID authenticates user  
3. MFA + Conditional Access applied  
4. Entra issues SAML/OIDC tokens  
5. AWS establishes session  
6. Permission Sets applied  
7. User receives **temporary**, **least-privilege**, **rotating credentials**  

This eliminates IAM Users forever.

---

# 🔒 Why Identity Center Matters in Zero Trust

### ✔ No long-term access keys  
### ✔ No IAM passwords  
### ✔ No static roles  
### ✔ No manual user management  
### ✔ No privilege drift  
### ✔ Policy evaluation done OUTSIDE AWS  

Identity Center + Entra ID = Zero Trust foundation.

---

# 🚀 Next Chapter  
➡️ **Chapter 03 — Microsoft Entra ID Overview**  
[Next → 03-entra-id-overview.md](03-entra-id-overview.md)

⬅️ **Back to Chapter 01**  
[01-identity-foundations.md](01-identity-foundations.md)

---

# 🧭 SecureTheCloud Footer  
*(Same footer as Chapter 01 — omitted here for brevity, but paste it)*  
