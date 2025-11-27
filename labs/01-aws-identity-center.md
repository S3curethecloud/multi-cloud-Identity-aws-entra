# 🧪 SecureTheCloud Academy — Volume 1  
## **Lab 01 — Configure AWS IAM Identity Center (SSO)**  
Zero Trust Identity Layer

---

<div align="center">

![Identity Banner](../diagrams/identity-banner.png)

📺 **Watch the Full Lab Walkthrough:**  
https://www.youtube.com/@SecureTheCloud-dev

</div>

---

# 🎯 **Objective**

In this lab, you will:

- Enable **AWS IAM Identity Center (formerly AWS SSO)**
- Configure your initial identity settings
- Prepare AWS for external federation from Microsoft Entra ID (Azure AD)
- Locate the SCIM and SSO URLs needed in later labs
- Validate Identity Center is ready for federation

This is *required* before connecting Microsoft Entra ID in Lab 02.

---

# 🧩 **Prerequisites**

### ✔ AWS Root user (you are using this — good)  
### ✔ AWS Organizations is automatically enabled  
### ✔ No existing Identity Center configuration  
### ✔ Multi-Cloud Compute Layer (Volume 0) completed  

---

# 🚀 **Step 1 — Log in to AWS Console (Root Account)**

1. Open: https://console.aws.amazon.com  
2. Log in as **root user**  
3. Ensure you're in the **management account** (top right → AWS Account)

Expected:  
You see “My Organization” on the left sidebar.

---

# 🚀 **Step 2 — Navigate to AWS IAM Identity Center**

1. From AWS Console Home  
2. Search for:

