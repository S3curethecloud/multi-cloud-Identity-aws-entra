# 📘 CHAPTER 04 — Federation Theory (SAML • OIDC • SCIM)
### *SecureTheCloud Identity Academy — Volume 1*

---
```mermaid
graph TD
    A[Federation Theory] --> B[Core Concepts]
    A --> C[Protocols & Standards]
    A --> D[Identity Lifecycle]
    
    B --> B1[Single Sign-On]
    B --> B2[Trust Relationships]
    B --> B3[Identity Provider]
    B --> B4[Service Provider]
    B --> B5[Claims & Assertions]
    
    C --> C1[SAML 2.0]
    C1 --> C1_1[XML-Based]
    C1 --> C1_2[Enterprise Focus]
    C1 --> C1_3[Strong Security]
    C1 --> C1_4[Web SSO Profile]
    
    C --> C2[OpenID Connect]
    C2 --> C2_1[OAuth 2.0 Based]
    C2 --> C2_2[JSON/REST API]
    C2 --> C2_3[Web & Mobile]
    C2 --> C2_4[ID Tokens]
    
    C --> C3[SCIM 2.0]
    C3 --> C3_1[User Provisioning]
    C3 --> C3_2[RESTful API]
    C3 --> C3_3[CRUD Operations]
    C3 --> C3_4[Schema Definition]
    
    D --> D1[Create User]
    D --> D2[Update Profile]
    D --> D3[Group Management]
    D --> D4[Deactivate/Delete]
    
    %% Relationships between components
    C1 -.-> B1
    C2 -.-> B1
    C3 -.-> D1
    C3 -.-> D4
    
    B3 -.-> C1
    B3 -.-> C2
    B4 -.-> C1
    B4 -.-> C2
    
    %% Styling
    classDef theory fill:#e1f5fe
    classDef protocol fill:#f3e5f5
    classDef lifecycle fill:#e8f5e8
    classDef concept fill:#fff3e0
    
    class A,B theory
    class C,C1,C2,C3 protocol
    class D,D1,D2,D3,D4 lifecycle
    class B1,B2,B3,B4,B5 concept
```

# 🎯 Chapter Objective  
This chapter explains the three core protocols that make multi-cloud identity possible:

- **SAML** — Used for authentication (AuthN) between Entra ID and AWS  
- **OIDC** — Modern protocol for tokens and applications  
- **SCIM** — Automated user & group provisioning (identity lifecycle)

You will learn:

- How federation works  
- How AWS trusts Entra  
- Why tokens replace passwords  
- Why Identity Source = Entra ID  
- How AWS maps users → permission sets  
- How SCIM automates the workforce lifecycle  

---

# 🧩 **1. What is Federation?**

Federation means:

> **Using an external identity provider (IdP) to authenticate and authorize users into a service provider (SP).**

In Volume 1:

- **Microsoft Entra ID = IdP**  
- **AWS IAM Identity Center = SP**

This allows:

- ✔ SSO  
- ✔ Centralized identity  
- ✔ Unified governance  
- ✔ Zero passwords inside AWS  

Azure handles the identity.  
AWS handles the access.

---

# 🟦 **2. SAML — Security Assertion Markup Language**

SAML is an XML-based protocol used for:

- Authentication  
- Identity claims  
- SSO between IdP ↔ SP  

### AWS uses SAML for:
- Signing users into AWS console  
- Passing identity claims  
- Establishing trust between Entra ↔ IAM Identity Center  

### SAML Flow (Simplified)
---

User → Entra ID → SAML assertion → AWS → Role → Session

- **IdP** → Entra ID  
- **SP** → AWS IAM Identity Center  
- **Assertion** → Proof of identity  
- **Metadata** → XML configuration for trust  

This is old but **very stable** for enterprise federation.

---

# 🟦 **3. OIDC — OpenID Connect**

OIDC is the modern authentication protocol built on OAuth 2.0.

OIDC uses **JSON Web Tokens (JWT)** instead of XML.

### Uses:
- App authentication  
- API identity  
- Device login  
- SaaS apps  

### Why not used for AWS federation here?

AWS IAM Identity Center still requires **SAML** for workforce SSO.

OIDC is used for:

- Workload identity  
- Application identity  
- OAuth flows  
- External identity providers  

Later in Volume 3:
- Azure Conditional Access uses OIDC  
- Entra ID tokens → AWS sessions  

---

# 🟧 **4. SCIM — System for Cross-domain Identity Management**

SCIM handles:

### ✔ Automated user provisioning  
### ✔ Automated group provisioning  
### ✔ Attribute sync  
### ✔ Lifecycle management  

This is critical for Zero Trust identity lifecycle.

### SCIM Flow

**Entra ID → SCIM API → AWS IAM Identity Center**

AWS creates:

- Users  
- Groups  
- Group membership  

Automatically.

No manual IAM Users ever again.

---

# 🧠 **5. How Identity Federation Works in AWS**

### Step 1 — Entra ID authenticates user  
MFA, Conditional Access, risk evaluation.

### Step 2 — SAML token sent to AWS  
Contains user identity + attributes.

### Step 3 — AWS IAM Identity Center maps user → Permission Sets  
Authorization happens here.

### Step 4 — SCIM maintains user + group lifecycle  
Admins never manually create IAM users.

---

# 🛡️ **6. Zero Trust Integration**

Federation enforces:

- Verified identity  
- MFA  
- Conditional Access policies  
- Session risk evaluation  
- Device compliance  
- Enforced least privilege  
- Automated offboarding  

Together:

> Federation + SCIM + Conditional Access = Zero Trust Identity Core

---

# 📚 Summary

| Protocol | Purpose | Used in Volume 1 |
|---------|---------|------------------|
| **SAML** | Federation AuthN | Yes (AWS SSO login) |
| **OIDC** | Token-based AuthN | Yes (later in CA) |
| **SCIM** | User/Group Provisioning | Yes (Lab 03) |

---

# ⬅️ Next Chapter  
👉 **Chapter 05 — Identity Governance & Conditional Access**
