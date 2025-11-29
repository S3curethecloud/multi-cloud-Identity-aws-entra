🛡️ SecureTheCloud Identity Academy — Volume 1
Lab 03 — SCIM Provisioning (Microsoft Entra → AWS IAM Identity Center)

<div align="center">

![Identity Banner](../diagrams/identity-banner.png)


Zero Trust Identity Layer


🔗 https://SecureTheCloud.dev

📺 https://www.youtube.com/@SecureTheCloud-dev

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

Your objective in this lab is to configure SCIM Provisioning from Microsoft Entra ID to AWS IAM Identity Center.

🗺️ SCIM Provisioning Architecture Map (Clickable)

(Click to expand)

<details> <summary><strong>🗺️ Click to Expand SCIM Provisioning Diagram</strong></summary>

    ```mermaid
flowchart LR
    A["<a href='02-entra-enterprise-app.md'>Entra Enterprise App</a>"] -->|SCIM Token| B["<a href='03-scim-provisioning.md'>SCIM Provisioning</a>"]
    B -->|Sync Users| C["<a href='../theory/04-federation-theory.md'>AWS IAM Identity Center</a>"]
    C --> D["<a href='../theory/06-permission-sets-rbac.md'>Permission Sets</a>"]
    ```

</details>
🧩 Prerequisites

Before starting, ensure you completed:

✔ Lab 01 — AWS IAM Identity Center

✔ Lab 02 — Enterprise App (SAML Federation)

✔ SCIM URL (captured in Lab 01)

✔ SCIM Access Token (generated from AWS Identity Center)

✔ Entra ID Admin permissions

✔ At least one Entra Security Group created (e.g., AWS-Developers)

🚀 Step 1 — Open Your Enterprise App in Entra ID

Visit: https://entra.microsoft.com

Go to: Identity → Applications → Enterprise Applications

Select the Enterprise App created in Lab 02 (example: SecureTheCloud)

You should now be on the application Overview page.

🚀 Step 2 — Open the Provisioning Blade

From the left navigation menu:

Provisioning → Overview

Under Provisioning Mode select:

✔ Automatic

This tells Entra:

“I will sync objects into AWS IAM Identity Center using SCIM.”

🚀 Step 3 — Enter the SCIM Configuration

Navigate to:

AWS IAM Identity Center → Settings → Identity Source

Copy the following info:

🔹 SCIM Endpoint

Example:

https://scim.<region>.amazonaws.com/scim/v2/

🔹 SCIM Access Token

Paste exactly as generated.
⚠️ Never upload your SCIM token to GitHub or anywhere public.

Paste both values into:

Provisioning → Admin Credentials

Click Test Connection.

🚀 Step 4 — Save & Start Provisioning

After the connection test succeeds:

Click Save

Click Start Provisioning

Entra ID will begin pushing:

Users

Groups

Group memberships

into AWS IAM Identity Center automatically.

Provisioning runs every 40 minutes by default.

🔍 Validate SCIM Sync

Navigate in AWS Console:

IAM Identity Center → Groups

You should see:

AWS-Developers

AWS-Admins

AWS-ReadOnly

Any custom groups created

These were synced via SCIM.

🎉 Lab Completion Checklist

✔ SCIM connection established
✔ Test Connection succeeded
✔ Groups synced
✔ Users synced
✔ Zero manual IAM users created
✔ Ready for Permission Sets (Lab 04)

➡️ Next Lab

📘 Lab 04 — Permission Sets Assignment
👉 04-permission-sets.md

🔙 Back to Identity Theory

📘 Federation Theory — Chapter 04

📘 Permission Sets — Chapter 06

<div align="center">

© 2025 SecureTheCloud.dev — All Rights Reserved
Zero Trust • Multi-Cloud • Enterprise Architecture

Terms
 •
Privacy
 •
Status
 •
Community
 •
Docs

</div>
