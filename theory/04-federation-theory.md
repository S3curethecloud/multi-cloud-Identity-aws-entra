# 🧩 SecureTheCloud Academy — Volume 1  
## **Chapter 04 — Federation Theory: SAML • OIDC • SCIM**

---

<div align="center">

![Identity Banner](../diagrams/identity-banner.png)

📺 **Watch the Federation Theory Lesson:**  
https://www.youtube.com/@SecureTheCloud-dev

</div>

---

# 🌍 Overview

Identity federation enables one identity provider (IdP) to authenticate users for multiple service providers (SPs).  
In Volume 1, federation allows:

- **Microsoft Entra ID** → authenticate users  
- **AWS IAM Identity Center** → trust the authentication  
- **SCIM** → sync the identities into AWS  
- **Permission Sets** → map the authorization  

This chapter explains the protocols behind federation.

---

# 🔐 The Three Lanes of Cloud Identity Integration

### **1️⃣ Authentication (Federation) → SAML / OIDC**  
Confirms *who* the user is.

### **2️⃣ Provisioning → SCIM 2.0**  
Syncs *who* exists (users, groups).

### **3️⃣ Authorization → Permission Sets**  
Enforces *what they can do*.

All three are required for Zero Trust identity.

---

# 🟣 SAML 2.0 (Security Assertion Markup Language)

Used for:

- Browser-based authentication  
- Federation between IdP → SP  
- XML assertions  

### How SAML Works (High-Level)

1. User attempts to access AWS  
2. AWS redirects to Entra ID  
3. User authenticates + MFA  
4. Entra issues a **SAML assertion**  
5. AWS validates the assertion  
6. AWS issues temporary session  

### SAML Assertion Contains:

- User identifier  
- Groups  
- Claims  
- Token lifetime  
- Session metadata  

AWS IAM Identity Center uses SAML for its external IdP sign-in.

---

# 🔵 OIDC (OpenID Connect)

Used for:

- Modern authentication  
- API/web app sign-in  
- JWT tokens  
- OAuth2 extensions  

### OIDC Token Types:

- **ID Token (JWT)**  
- **Access Token**  
- **Refresh Token**  

OIDC is lighter, faster, and JSON-based — unlike SAML (XML).

### AWS Usage:

AWS does not use OIDC for Identity Center sign-in today (still SAML),  
but uses OIDC heavily for:

- Cognito  
- App integrations  
- Third-party identity platforms  
- Workload identity  

---

# 🟢 SCIM 2.0 (System for Cross-domain Identity Management)

Provisioning protocol for:

- Users  
- Groups  
- Membership  
- Updates  
- Deletions  

### SCIM Handles:

- User creation  
- Group creation  
- Group membership  
- User updates  
- Deactivation  
- Soft deletion  

### In SecureTheCloud:

Microsoft Entra ID → SCIM → AWS Identity Center

SCIM ensures AWS always reflects the authoritative identity state from Entra.

---

# 🔁 End-to-End Identity Lifecycle With Federation + SCIM

1. User is created in Entra ID  
2. SCIM sync creates user in AWS Identity Center  
3. Group membership syncs  
4. SSO via SAML authenticates user  
5. Permission Sets grant least privilege  
6. Changes in Entra sync back instantly  
7. Deleting user in Entra → removes AWS access  

You get **full Zero Trust lifecycle control**.

---

# 🚀 Next Chapter  
➡️ **Chapter 05 — Zero Trust Identity Principles**  
[05-zero-trust-identity.md](05-zero-trust-identity.md)

⬅️ **Back to Chapter 03**  
[03-entra-id-overview.md](03-entra-id-overview.md)

---

# 🔙 Back to README  
https://github.com/S3curethecloud/multi-cloud-identity-aws-entra

---

# 🧭 SecureTheCloud Footer

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
