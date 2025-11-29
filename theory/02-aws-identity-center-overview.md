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
    A[<b>AWS IAM Identity Center</b><br/>Formerly AWS SSO]:::root

    %% ======================
    %% CORE COMPONENTS
    %% ======================
    A --> B1[Identity Source]:::identity
    A --> B2[Users & Groups]:::users
    A --> B3[Permission Sets]:::permissions
    A --> B4[AWS Accounts]:::accounts
    A --> B5[Applications]:::apps
    A --> B6[Authentication Flow]:::auth

    %% ======================
    %% IDENTITY SOURCE
    %% ======================
    B1 --> C1[Entra ID<br/>External IdP]:::idp
    B1 --> C2[AWS Identity Center Directory]:::directory
    B1 --> C3[SCIM Provisioning Setup]:::provisioning
    B1 --> C4[SAML / OIDC Federation]:::federation

    %% ======================
    %% USERS & GROUPS
    %% ======================
    B2 --> D1[Synchronized Users<br/>via SCIM]:::sync
    B2 --> D2[Synchronized Groups<br/>Security Groups]:::groups
    B2 --> D3[Dynamic Role Mapping]:::mapping

    %% ======================
    %% PERMISSION SETS
    %% ======================
    B3 --> E1[AWS Managed Policies]:::managed
    B3 --> E2[Custom JSON Policies]:::custom
    B3 --> E3[Session Duration]:::session
    B3 --> E4[Inline Permissions]:::inline
    B3 --> E5[RBAC Role Modeling]:::rbac

    %% ======================
    %% AWS ACCOUNTS
    %% ======================
    B4 --> F1[OU Mappings]:::ou
    B4 --> F2[Account Assignments]:::assignment
    B4 --> F3[Least Privilege Boundaries]:::security

    %% ======================
    %% APPLICATIONS
    %% ======================
    B5 --> G1[AWS Console]:::console
    B5 --> G2[AWS CLI v2<br/>SSO Login]:::cli
    B5 --> G3[AWS SDK Integration]:::sdk
    B5 --> G4[SAML Apps]:::saml

    %% ======================
    %% AUTHENTICATION FLOW
    %% ======================
    B6 --> H1[User Requests Access]:::step1
    H1 --> H2[Redirect to Entra ID IdP]:::step2
    H2 --> H3[MFA + Policy Evaluation]:::step3
    H3 --> H4[Token Issued OIDC/SAML]:::step4
    H4 --> H5[Identity Center Maps Roles<br/>Permission Sets]:::step5
    H5 --> H6[User Receives Console/CLI Access]:::step6
    H6 --> H7[Zero Trust Enforcement<br/>Before Access Granted]:::step7

    %% ======================
    %% COLORFUL STYLES
    %% ======================
    classDef root fill:#FF6B6B,stroke:#FF4757,color:white,font-weight:bold,stroke-width:3px
    classDef identity fill:#4ECDC4,stroke:#45B7AA,color:black,stroke-width:2px
    classDef users fill:#FFE66D,stroke:#FFD93D,color:black,stroke-width:2px
    classDef permissions fill:#6A67CE,stroke:#575FCF,color:white,stroke-width:2px
    classDef accounts fill:#1DD1A1,stroke:#10AC84,color:black,stroke-width:2px
    classDef apps fill:#FF9FF3,stroke:#F368E0,color:black,stroke-width:2px
    classDef auth fill:#54A0FF,stroke:#2E86DE,color:white,stroke-width:2px
    
    classDef idp fill:#00D2D3,stroke:#01A3A4,color:black
    classDef directory fill:#5F27CD,stroke:#341F97,color:white
    classDef provisioning fill:#FF9F43,stroke:#F39C12,color:black
    classDef federation fill:#EE5A24,stroke:#EA2027,color:white
    
    classDef sync fill:#A3CB38,stroke:#7B9E30,color:black
    classDef groups fill:#ED4C67,stroke:#B53447,color:white
    classDef mapping fill:#0652DD,stroke:#0344BB,color:white
    
    classDef managed fill:#FFC312,stroke:#E0AC0D,color:black
    classDef custom fill:#C4E538,stroke:#A3CB0B,color:black
    classDef session fill:#12CBC4,stroke:#0DA8A2,color:black
    classDef inline fill:#FDA7DF,stroke:#F08CC9,color:black
    classDef rbac fill:#9980FA,stroke:#7A67D8,color:white
    
    classDef ou fill:#FF6B81,stroke:#EE5A6F,color:white
    classDef assignment fill:#5758BB,stroke:#4546A6,color:white
    classDef security fill:#009432,stroke:#006266,color:white
    
    classDef console fill:#FF9F1A,stroke:#E08E0B,color:black
    classDef cli fill:#2ED573,stroke:#25A55A,color:black
    classDef sdk fill:#3742FA,stroke:#2F36D1,color:white
    classDef saml fill:#FF3838,stroke:#E82C2C,color:white
    
    classDef step1 fill:#70A1FF,stroke:#5352ED,color:white
    classDef step2 fill:#7BED9F,stroke:#2ED573,color:black
    classDef step3 fill:#FF6B81,stroke:#FF4757,color:white
    classDef step4 fill:#FF9F1A,stroke:#FF7F00,color:black
    classDef step5 fill:#5352ED,stroke:#3742FA,color:white
    classDef step6 fill:#2ED573,stroke:#25A55A,color:black
    classDef step7 fill:#FF6348,stroke:#FF3F34,color:white

    %% ======================
    %% APPLY CLASSES
    %% ======================
    class A root
    class B1 identity
    class B2 users
    class B3 permissions
    class B4 accounts
    class B5 apps
    class B6 auth
    
    class C1 idp
    class C2 directory
    class C3 provisioning
    class C4 federation
    
    class D1 sync
    class D2 groups
    class D3 mapping
    
    class E1 managed
    class E2 custom
    class E3 session
    class E4 inline
    class E5 rbac
    
    class F1 ou
    class F2 assignment
    class F3 security
    
    class G1 console
    class G2 cli
    class G3 sdk
    class G4 saml
    
    class H1 step1
    class H2 step2
    class H3 step3
    class H4 step4
    class H5 step5
    class H6 step6
    class H7 step7
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
