<div align="center">

<img src="../diagrams/securethecloud-banner.png" alt="SecureTheCloud Banner" width="100%"/>

# **SecureTheCloud Identity Academy — Volume 1**
### **AWS IAM Identity Center ↔ Microsoft Entra ID — SCIM User & Group Provisioning**

🔗 https://SecureTheCloud.dev  
📺 https://www.youtube.com/@SecureTheCloud-dev  

---

</div>

```mermaid
flowchart LR
    A["<a href='../02-entra-enterprise-app.md'>Entra<br/>Enterprise App</a>"]:::start
    B["<a href='../01-aws-identity-center.md'>AWS IAM Identity Center<br/>(SP)</a>"]:::core
    C["<a href='#step-3-enter-the-scim-configuration'>SCIM Endpoint</a>"]:::step
    D["<a href='#step-3-enter-the-scim-configuration'>SCIM Access Token</a>"]:::step
    E["<a href='#step-4-validate-scim-sync'>Sync Users</a>"]:::step
    F["<a href='#step-4-validate-scim-sync'>Sync Groups</a>"]:::step
    G["<a href='../README.md'>Return to Volume 1</a>"]:::return

    %% FLOW
    A --> C
    A --> D
    C --> E
    D --> E
    E --> F
    F --> B
    B --> G

    %% STYLES
    classDef start fill:#1B4F72,stroke:#fff,color:#fff,font-weight:bold
    classDef core fill:#21618C,stroke:#fff,color:white,font-weight:bold
    classDef step fill:#EBF5FB,stroke:#1B4F72,color:#1B2631
    classDef return fill:#F9EBEA,stroke:#922B21,color:#922B21,font-weight:bold
    ```
📘 Overview
SCIM (System for Cross-Domain Identity Management) enables:

✔ Automatic user creation
✔ Automatic group creation
✔ Automatic user → group membership sync
✔ Automatic deactivation
✔ No manual IAM users
✔ No drift
✔ Zero Shadow Identities
✔ True Zero Trust Workforce Identity

This lab configures SCIM Provisioning from Microsoft Entra to AWS IAM Identity Center.

🧱 Prerequisites
Before starting, complete:

✔ Lab 01 — AWS IAM Identity Center
✔ Lab 02 — Microsoft Entra Enterprise App (SAML Federation)
✔ AWS SSO URL (captured in Lab 01)
✔ SCIM URL (from AWS Identity Center)
✔ SCIM Access Token (from AWS Identity Center)
✔ Entra Admin permissions
✔ At least one Entra Security Group created
🚀 Step 1 — Open the Enterprise App in Microsoft Entra
Visit
https://entra.microsoft.com

Go to:
Identity → Applications → Enterprise Applications

Select the app you created in Lab 02 (e.g., SecureTheCloud)

You should land on the Overview page.

🚀 Step 2 — Open the Provisioning Blade
On the left navigation menu:

Provisioning → Overview

Under Provisioning Mode, choose:

Automatic

This tells Entra:

✔ “I will sync objects into AWS IAM Identity Center using SCIM.”

🚀 Step 3 — Enter the SCIM Configuration
<a id="step-3-enter-the-scim-configuration"></a>

From AWS IAM Identity Center:

Settings → Identity Source → SCIM

Copy the following into Entra:

🔹 SCIM Endpoint
Example:

bash
Copy code
https://scim.<region>.amazonaws.com/scim/v2/<GUID>
🔹 SCIM Access Token
Paste exactly as generated from AWS.

⚠️ Never upload tokens to GitHub.

After entering both values:

➡️ Click Test Connection
➡️ Expected result: Connection successful

🚀 Step 4 — Validate SCIM Sync
<a id="step-4-validate-scim-sync"></a>

Scroll down in Entra to:

Mappings → Provision Azure Active Directory Users

Ensure:

✔ Enabled
✔ Attribute mappings look correct
✔ "Provisioning Status" shows Healthy

Now click:

Start Provisioning

Expected Results:
👤 Users
Entra automatically pushes synced users into:

AWS IAM Identity Center → Users

👥 Groups
Entra pushes Group info into:

AWS IAM Identity Center → Groups

You should see groups like:

AWS-Developers

AWS-Admins

AWS-ReadOnly

Any Custom SGs you created

✔ No manual IAM creation
✔ No drift
✔ Zero Trust lifecycle in place

🧪 Step 5 — Test SCIM End-to-End
Go to:

AWS IAM Identity Center → Groups

You should see synced groups and membership:

AWS-Developers (members from Entra)

AWS-Admins

Any custom groups

Then check:

Users → Assigned Groups

Identity MUST flow from:

IdP (Entra) → SP (AWS)

This validates:

✔ Federation
✔ SCIM
✔ Group mapping
✔ Zero Trust identity lifecycle

🧠 Lab Completion Checklist
Check	Item
✔	SCIM Endpoint configured
✔	SCIM Token configured
✔	Test Connection successful
✔	Sync started
✔	Users synced
✔	Groups synced
✔	No errors in provisioning logs
✔	Identity flow established (IdP → SP)

🎉 Next Lab — Permission Sets Assignment (RBAC at Scale)
👉 Proceed to:
🔗 Lab 04 — Permission Sets Assignment
04-permission-sets.md

Or return to theory:

🔗 Chapter 05 — Zero Trust Identity Principles
🔗 Chapter 06 — Permission Sets & Enterprise RBAC

🏁 Back to Volume 1 Home
📘 https://github.com/S3curethecloud/multi-cloud-Identity-aws-entra

<div align="center">

© 2025 SecureTheCloud.dev — All Rights Reserved
Zero Trust • Multi-Cloud • Enterprise Architecture

Terms •
Privacy •
Status •
Community •
Docs

</div>
