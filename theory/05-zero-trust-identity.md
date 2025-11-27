# 🧩 SecureTheCloud Academy — Volume 1  
## **Chapter 05 — Zero Trust Identity Principles**

---

<div align="center">

![Identity Banner](../diagrams/identity-banner.png)

📺 **Watch the Zero Trust Identity Lesson:**  
https://www.youtube.com/@SecureTheCloud-dev

</div>

---

# 🌍 Overview

Zero Trust = “Never trust, always verify.”

Identity is the **#1 enforcement point** in modern security architecture.

This chapter explains how Zero Trust applies to AWS, Azure, and multi-cloud identity federation.

---

# 🔐 The Three Zero Trust Principles

### **1️⃣ Verify Explicitly**  
Authenticate every session with:

- MFA  
- Conditional Access  
- Device compliance  
- IP and location evaluation  
- Token freshness  
- Real-time risk assessment  

### **2️⃣ Use Least Privilege Access**  
Enforced through:

- AWS Permission Sets  
- Scoped roles  
- JIT credentials  
- Short session durations  
- Policy boundaries  

### **3️⃣ Assume Breach**  
Enforced by:

- Conditional Access  
- Identity Protection  
- Continuous monitoring  
- AWS CloudTrail  
- Entra risk scoring  

Identity mesh becomes the **primary security boundary**.

---

# 🔄 Zero Trust Identity Workflow

1. User attempts login  
2. Conditional Access evaluates context  
3. MFA enforced  
4. Token issued  
5. AWS validates SAML  
6. Permission Sets define authorization  
7. Session expires (short TTL)  
8. Re-authorization required  

Zero Trust = No long sessions, no bypass, no implicit trust.

---

# 🛡️ Identity Threat Protection

Microsoft Entra ID + AWS provides:

- Impossible travel detection  
- Device risk detection  
- Phishing-resistant MFA  
- Token theft detection  
- Sign-in frequency rules  
- Session risk detection  
- Automated account lockouts  

---

# 🌐 Zero Trust Across Clouds

AWS Identity Center trusts Entra ID.  
Therefore:

**Zero Trust applied in Entra automatically enforces Zero Trust in AWS.**

This is why federation MATTERS.

---

# 🚀 Next Chapter  
➡️ **Chapter 06 — Permission Sets & Enterprise RBAC**  
[06-permission-sets-enterprise-rbac.md](06-permission-sets-enterprise-rbac.md)

⬅️ Back to Chapter 04  
[04-federation-theory.md](04-federation-theory.md)

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
