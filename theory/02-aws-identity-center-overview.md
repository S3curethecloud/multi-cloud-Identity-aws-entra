# 🧩 SecureTheCloud Academy — Volume 1  
## **Chapter 02 — AWS IAM Identity Center Overview**

---

<div align="center">

![Identity Banner](../diagrams/identity-banner.png)

📺 **Watch the AWS Identity Center Lesson:**  
https://www.youtube.com/@SecureTheCloud-dev

</div>

---

```mermaid
flowchart TD
%% ======================
%% ROOT
%% ======================
A[<b>AWS IAM Identity Center</b><br/>(Formerly AWS SSO]:::root

%% ======================
%% CORE COMPONENTS
%% ======================
A --> B1[Identity Source]
A --> B2[Users & Groups]
A --> B3[Permission Sets]
A --> B4[AWS Accounts]
A --> B5[Applications]
A --> B6[Authentication Flow]

%% STYLE
classDef root fill:#1F618D,stroke:#fff,color:white,font-weight:bold;
classDef section fill:#EAF2F8,stroke:#1B4F72,color:#1B2631;
classDef item fill:#FDFEFE,stroke:#2E4053,color:#2E4053;

%% ======================
%% IDENTITY SOURCE
%% ======================
B1 --> C1[Entra ID<br/>(External IdP)]:::item
B1 --> C2[AWS Identity Center Directory]:::item
B1 --> C3[SCIM Provisioning Setup]:::item
B1 --> C4[SAML / OIDC Federation]:::item

%% ======================
%% USERS & GROUPS
%% ======================
B2 --> D1[Synchronized Users<br/>(via SCIM)]:::item
B2 --> D2[Synchronized Groups<br/>(Security Groups)]:::item
B2 --> D3[Dynamic Role Mapping]:::item

%% ======================
%% PERMISSION SETS
%% ======================
B3 --> E1[AWS Managed Policies]:::item
B3 --> E2[Custom JSON Policies]:::item
B3 --> E3[Session Duration]:::item
B3 --> E4[Inline Permissions]:::item
B3 --> E5[RBAC Role Modeling]:::item

%% ======================
%% AWS ACCOUNTS
%% ======================
B4 --> F1[OU Mappings]:::item
B4 --> F2[Account Assignments]:::item
B4 --> F3[Least Privilege Boundaries]:::item

%% ======================
%% APPLICATIONS
%% ======================
B5 --> G1[AWS Console]:::item
B5 --> G2[AWS CLI v2<br/>SSO Login]:::item
B5 --> G3[AWS SDK Integration]:::item
B5 --> G4[SAML Apps]:::item

%% ======================
%% AUTHENTICATION FLOW
%% ======================
B6 --> H1[User Requests Access]:::item
H1 --> H2[Redirect to Entra ID (IdP)]:::item
H2 --> H3[MFA + Policy Evaluation]:::item
H3 --> H4[Token Issued (OIDC/SAML)]:::item
H4 --> H5[Identity Center Maps Roles<br/>→ Permission Sets]:::item
H5 --> H6[User Receives Console/CLI Access]:::item
H6 --> H7[Zero Trust Enforcement<br/>Before Access Granted]:::item

%% ======================
%% LEGEND
%% ======================
A:::root
```



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
