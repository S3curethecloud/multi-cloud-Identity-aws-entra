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
A["<a href='../README.md'>AWS IAM Identity Center<br/>(Formerly AWS SSO)</a>"]:::root

%% ======================
%% CORE COMPONENTS
%% ======================
A --> B1["<a href='04-federation-theory.md'>Identity Source</a>"]
A --> B2["<a href='04-federation-theory.md#users-and-groups'>Users and Groups</a>"]
A --> B3["<a href='06-permission-sets-rbac.md'>Permission Sets</a>"]
A --> B4["<a href='02-aws-identity-center-overview.md#aws-accounts'>AWS Accounts</a>"]
A --> B5["<a href='02-aws-identity-center-overview.md#applications'>Applications</a>"]
A --> B6["<a href='04-federation-theory.md#authentication-flow'>Authentication Flow</a>"]

%% ======================
%% STYLE DEFINITIONS
%% ======================
classDef root fill:#1F618D,stroke:#ffffff,color:#ffffff,font-weight:bold;
classDef section fill:#EAF2F8,stroke:#1B4F72,color:#1B2631;
classDef item fill:#FDFEFE,stroke:#2E4053,color:#2E4053;

%% ======================
%% IDENTITY SOURCE (CLICKABLE)
%% ======================
B1 --> C1["<a href='04-federation-theory.md#identity-provider-idp'>Entra ID (External IdP)</a>"]:::item
B1 --> C2["<a href='02-aws-identity-center-overview.md#aws-identity-center-directory'>AWS Identity Center Directory</a>"]:::item
B1 --> C3["<a href='../labs/03-scim-provisioning.md'>SCIM Provisioning Setup</a>"]:::item
B1 --> C4["<a href='../labs/02-entra-enterprise-app.md'>SAML or OIDC Federation</a>"]:::item

%% ======================
%% USERS & GROUPS (CLICKABLE)
%% ======================
B2 --> D1["<a href='../labs/03-scim-provisioning.md#provisioning-users'>Provisioned Users (SCIM)</a>"]:::item
B2 --> D2["<a href='../labs/03-scim-provisioning.md#provisioning-groups'>Provisioned Groups</a>"]:::item
B2 --> D3["<a href='06-permission-sets-rbac.md#group-to-role-mapping'>Group → Role Mapping</a>"]:::item

%% ======================
%% PERMISSION SETS (CLICKABLE)
%% ======================
B3 --> E1["<a href='06-permission-sets-rbac.md#aws-managed-policies'>AWS Managed Policies</a>"]:::item
B3 --> E2["<a href='06-permission-sets-rbac.md#custom-policies'>Custom JSON Policies</a>"]:::item
B3 --> E3["<a href='06-permission-sets-rbac.md#session-duration'>Session Duration</a>"]:::item
B3 --> E4["<a href='06-permission-sets-rbac.md#inline-permissions'>Inline Permissions</a>"]:::item
B3 --> E5["<a href='06-permission-sets-rbac.md#rbac-hierarchy'>RBAC Role Modeling</a>"]:::item

%% ======================
%% AWS ACCOUNTS (CLICKABLE)
%% ======================
B4 --> F1["<a href='02-aws-identity-center-overview.md#organizational-units-ous'>Organizational Units</a>"]:::item
B4 --> F2["<a href='../labs/01-aws-identity-center.md#account-assignments'>Account Assignments</a>"]:::item
B4 --> F3["<a href='06-permission-sets-rbac.md#least-privilege'>Least Privilege Boundaries</a>"]:::item

%% ======================
%% APPLICATIONS (CLICKABLE)
%% ======================
B5 --> G1["<a href='../labs/01-aws-identity-center.md#aws-console-access'>AWS Console</a>"]:::item
B5 --> G2["<a href='02-aws-identity-center-overview.md#aws-cli-sso'>AWS CLI SSO Login</a>"]:::item
B5 --> G3["<a href='02-aws-identity-center-overview.md#sdk-integration'>AWS SDK Integration</a>"]:::item
B5 --> G4["<a href='../labs/02-entra-enterprise-app.md#saml-applications'>SAML Apps</a>"]:::item

%% ======================
%% AUTHENTICATION FLOW (CLICKABLE)
%% ======================
B6 --> H1["<a href='04-federation-theory.md#user-authentication-flow'>User Initiates Access</a>"]:::item
H1 --> H2["<a href='04-federation-theory.md#redirect-to-idp'>Redirect to Entra ID</a>"]:::item
H2 --> H3["<a href='04-federation-theory.md#mfa-policy-evaluation'>MFA + Policy Evaluation</a>"]:::item
H3 --> H4["<a href='04-federation-theory.md#oidc-token-issuance'>OIDC or SAML Token Issued</a>"]:::item
H4 --> H5["<a href='06-permission-sets-rbac.md#permission-set-mapping'>Permission Set Mapping</a>"]:::item
H5 --> H6["<a href='../labs/01-aws-identity-center.md#console-or-cli-access'>Console or CLI Access</a>"]:::item
H6 --> H7["<a href='01-identity-foundations.md#zero-trust'>Zero Trust Enforcement</a>"]:::item

%% APPLY ROOT STYLE
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
