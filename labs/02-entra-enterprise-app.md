# 🧪 SecureTheCloud Academy — Volume 1  
## **Lab 02 — Create Microsoft Entra Enterprise App (AWS Federation)**  
Zero Trust Identity Layer

---

<div align="center">

![Identity Banner](../diagrams/identity-banner.png)

📺 **Watch the Full Lab Walkthrough:**  
https://www.youtube.com/@SecureTheCloud-dev

</div>

---

# 🎯 **Objective**

In this lab, you will configure:

- A **Microsoft Entra Enterprise Application** for AWS IAM Identity Center  
- Federation (SAML 2.0) from Entra → AWS  
- Token/claim settings for AWS  
- User/group assignment for SSO testing  
- Metadata exchange required for federation  
- Preparation for SCIM provisioning (Lab 03)

This is the *core* step in enabling Zero Trust authentication for AWS.

---

# 🧩 **Prerequisites**

Before starting, you must have completed:

### ✔ Lab 01 — Configure AWS IAM Identity Center  
### ✔ Volume 0 — Multi-Cloud Compute Layer  
### ✔ Entra ID Admin permissions  
### ✔ AWS SSO URL (captured in Lab 01)  
### ✔ AWS Region (confirm: `us-east-1` or your selected region)

---

# 🚀 **Step 1 — Sign in to Microsoft Entra Admin Center**

1. Open:  
   https://entra.microsoft.com  
2. Sign in with your **Global Admin** or **Application Administrator** account  
3. Confirm you're in the correct tenant:  
   **Tenant ID:** `776f9ea5-7add-469d-bc51-8e855e9a1d26`

Expected:

- Left sidebar shows **Identity**, **Applications**, **Users**, **Groups**

---

# 🚀 **Step 2 — Go to Enterprise Applications**

1. From left menu:  
   **Identity → Applications → Enterprise applications**
2. Click **+ New application**
3. Select: **Create your own application**

You will see a dialog:

> **Name your application**

Enter:

