# 🧩 SecureTheCloud Academy — Volume 1  
## **Chapter 01 — Identity Foundations**  
Zero Trust Identity Layer

---

<div align="center">

![Identity Banner](../diagrams/identity-banner.png)

📺 **Watch the Identity Foundations Lesson:**  
https://www.youtube.com/@SecureTheCloud-dev

</div>

---

```mermaid
flowchart TD

%% =============================
%% STC BRAND COLORS
%% =============================
classDef stcBlue fill:#1F618D,stroke:#ffffff,color:white;
classDef gold fill:#F4B400,stroke:#ffffff,color:black;
classDef teal fill:#1ABC9C,stroke:#ffffff,color:black;
classDef slate fill:#2C3E50,stroke:#ffffff,color:white;
classDef grey fill:#BDC3C7,stroke:#2C3E50,color:black;
classDef orange fill:#E67E22,stroke:#ffffff,color:white;

%% =============================
%% ROOT SECTION
%% =============================
A["<a href='../README.md'>Identity Foundations</a>"]:::stcBlue

A --> B["<a href='01-identity-foundations.md#authentication-vs-authorization'>Authn vs Authz</a>"]:::gold
A --> C["<a href='01-identity-foundations.md#identity-planes'>Identity Planes</a>"]:::teal
A --> D["<a href='01-identity-foundations.md#identity-lifecycle'>Identity Lifecycle</a>"]:::orange
A --> E["<a href='01-identity-foundations.md#cloud-identity'>Cloud Identity Models</a>"]:::slate

%% =============================
%% Authn vs Authz
%% =============================
B --> B1["Authentication:<br/>Are you who you claim?"]:::gold
B --> B2["Authorization:<br/>What can you do?"]:::gold

%% =============================
%% Identity Planes
%% =============================
C --> C1["Control Plane<br/>(Entra ID)"]:::teal
C --> C2["Access Plane<br/>(AWS IAM Identity Center)"]:::teal

%% =============================
%% Identity Lifecycle
%% =============================
D --> D1["Create"]:::orange
D --> D2["Update"]:::orange
D --> D3["Deactivate/Delete"]:::orange

%% =============================
%% Cloud Identity Models
%% =============================
E --> E1["Identity Provider (IdP)"]:::slate
E --> E2["Service Provider (SP)"]:::slate
E --> E3["Claims + Tokens"]:::slate
```

# 🌍 Overview  
Identity is the core control plane of all Zero Trust architectures.  
Before traffic is allowed, before permissions are granted, before data is accessed — **identity must be verified, authenticated, and authorized.**

In SecureTheCloud Volume 1, we unify:

- **Microsoft Entra ID (Azure AD)** → as the Enterprise Identity Provider (IdP)  
- **AWS IAM Identity Center** → as the Cloud Service Provider (SP)

This chapter explains the fundamentals that will support the federation, SCIM provisioning, RBAC design, and Zero Trust policies that follow.

---

# 🔐 What Is Identity in the Cloud?

Identity is no longer usernames and passwords.  
Identity is now:

- A **security perimeter**  
- A **source of truth**  
- A **policy evaluation engine**  
- A **risk evaluation mechanism**  
- A **Zero Trust enforcement point**

Identity includes:

### ✔ Users  
### ✔ Groups  
### ✔ Devices  
### ✔ Workloads  
### ✔ Service principals  
### ✔ Tokens  
### ✔ Claims  
### ✔ Session evaluation  

---

# 🧠 **Modern Identity Is Token-Based**

In Zero Trust identity platforms, authentication produces:

### ⭐ Tokens (not passwords)

Types include:

- **ID Token** (Who you are)  
- **Access Token** (What you can access)  
- **Refresh Token** (Extend your session)  

Tokens contain:

- **Claims**  
- **Issuer**  
- **Audience**  
- **Groups**  
- **Permissions**  
- **Conditional Access results**  

Identity = *the brain of your cloud architecture.*

---

# 🏛️ **Identity Provider (IdP)**  
An Identity Provider is responsible for:

- User authentication  
- MFA  
- Risk scoring  
- Token issuance  
- Conditional Access  
- Session lifetime  
- Policy enforcement  

For SecureTheCloud:

### **Microsoft Entra ID = The IdP**

Everything flows from Entra:

- Federation  
- SCIM  
- Conditional Access  
- Zero Trust rules  
- Graph-based provisioning  

---

# 🏢 **Service Provider (SP)**

A Service Provider consumes tokens issued by the IdP.

For SecureTheCloud:

### **AWS IAM Identity Center = The SP**

AWS relies on Entra for:

- Authentication  
- MFA  
- User identities  
- Groups  
- Provisioning  
- Permission Set mapping  

---

# 🔄 Identity Flow (High-Level)

1. User attempts to access AWS  
2. AWS redirects to Microsoft Entra SSO  
3. Entra performs MFA + policy evaluation  
4. Token is issued to AWS  
5. AWS maps identity to **Permission Sets**  
6. User receives *temporary, least-privilege credentials*  

This is the **modern Zero Trust identity handshake.**

---

# 🔁 Federation + Provisioning + Authorization

Identity integration consists of 3 layers:

### **1. Federation (Authentication)**  
OIDC / SAML → trusting authentication from Entra.

### **2. Provisioning (Identity Sync)**  
SCIM → syncing users & groups from Entra to AWS.

### **3. Authorization (Permissions)**  
Permission Sets → mapping identities to roles & access.

This course teaches all 3 with hands-on labs.

---

# 🚀 What’s Next?

Continue to:

➡️ **Chapter 02 — AWS IAM Identity Center Overview**  
[Next → 02-aws-identity-center-overview.md](02-aws-identity-center-overview.md)

---

# 🔙 Back to README  
https://github.com/S3curethecloud/multi-cloud-identity-aws-entra

---

# 🧭 **SecureTheCloud Footer**

<div align="center">

![Logo](../diagrams/securethecloud-logo.png)

**© 2025 SecureTheCloud.dev — All Rights Reserved**  
Zero Trust • Multi-Cloud • Enterprise Architecture  

[Terms](https://securethecloud.dev/terms) •  
[Privacy](https://securethecloud.dev/privacy) •  
[Status](https://securethecloud.dev/status) •  
[Community](https://t.me/SecureTheCloud) •  
[Docs](https://securethecloud.dev/docs)

</div>

