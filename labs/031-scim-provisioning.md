📘 LAB 03 — SCIM Provisioning (Microsoft Entra → AWS IAM Identity Center)
SecureTheCloud Identity Federation Academy — Volume 1
<div align="center">

</div>
🔗 Interactive Identity Architecture Map (Clickable)

```MERMAID
flowchart TD
A["<a href='../README.md'>SecureTheCloud Identity Layer</a>"] --> B["<a href='./02-entra-enterprise-app.md'>Lab 02<br>Entra Enterprise App</a>"]
B --> C["<a href='./03-scim-provisioning.md'>Lab 03<br>SCIM Provisioning</a>"]
C --> D["<a href='./04-permission-sets.md'>Lab 04<br>Permission Sets & RBAC</a>"]

%% Styles (matching Lab 2)
style A fill:#1F618D,stroke:#fff,stroke-width:2px,color:white
style B fill:#2874A6,stroke:#fff,color:white
style C fill:#1E8449,stroke:#fff,color:white
style D fill:#A93226,stroke:#fff,color:white
```

#️⃣ Lab 03 — SCIM Provisioning (Microsoft Entra → AWS)
Automatic user & group provisioning from Entra ID into AWS IAM Identity Center
🎯 Objective

In this lab, you will:

Enable Automatic Provisioning (SCIM 2.0) in AWS IAM Identity Center

Configure Entra ID to sync users/groups into AWS

Validate provisioning jobs

Sync identities instantly using Provision on Demand

Confirm AWS Identity Center receives:

Users

Groups

Group membership

This replaces all manual IAM user creation, enabling true Zero Trust Identity Lifecycle Management.

🧩 Prerequisites
✔ Completed Lab 01 — Configure AWS IAM Identity Center
✔ Completed Lab 02 — Entra Enterprise Application
✔ SCIM Endpoint URL (from AWS)
✔ SCIM Access Token (from AWS Identity Center)
✔ Microsoft Entra Admin privileges
✔ AWS Management Account Admin privileges
#️⃣ Step 1 — Collect SCIM Configuration Values from AWS

Log into AWS Console

Go to:
IAM Identity Center → Settings → Automatic Provisioning

Locate:

SCIM Endpoint URL
SCIM Access Token


Click:
Generate Token → Copy the token (⚠ do not save in GitHub)

These two values will be used in Entra ID.

#️⃣ Step 2 — Open the Entra Enterprise Application

Log into: https://entra.microsoft.com

Navigate to:
Identity → Applications → Enterprise Applications

Select your application:

AWS IAM Identity Center (SecureTheCloud)


In the left menu → Click Provisioning

You’ll see the provisioning blade with configuration options.

#️⃣ Step 3 — Enable Automatic Provisioning

Inside Provisioning:

Click Get Started

Set:

Provisioning Mode → Automatic


Two important fields appear:

Field	Value
Tenant URL	Paste AWS SCIM Endpoint
Secret Token	Paste SCIM Access Token

Click Test Connection

🟩 Expected:
✔ Successfully connected to the SCIM endpoint


If failed:

Token expired

Wrong AWS region

SCIM endpoint copied incorrectly

Entra enterprise app misconfigured (Lab 02)

#️⃣ Step 4 — Review Attribute Mappings
User Attributes (Default is correct):

userPrincipalName → userName

displayName → name.formatted

givenName → name.givenName

surname → name.familyName

mail → emails[type eq "work"].value

Group Attributes (Default is correct):

displayName → displayName

members → members

❗ Do not modify mappings unless your enterprise has custom identity schemas.

#️⃣ Step 5 — Start Provisioning

Scroll down and click:

Save


Then click:

Start Provisioning


Entra ID will now automatically sync users and groups to AWS every 40 minutes.

#️⃣ Step 6 — Assign Users & Groups to the Application

Provisioning only synchronizes assigned identities, so now:

Go to:
Enterprise App → Users and Groups

Click + Add user/group

Assign:

A test user

A test group

This triggers the provisioning process.

#️⃣ Step 7 — Provision Identities on Demand (Immediate Sync)

Automatic sync runs every 40 minutes, but you can force provisioning:

In the Provisioning blade → scroll down

Click:

Provision on Demand


Select a user

Click Provision

Expected:
✔ Successfully provisioned

#️⃣ Step 8 — Validate Provisioning in AWS

Return to AWS Console:

Navigate:
IAM Identity Center → Users
IAM Identity Center → Groups


You should now see:

👤 User appears automatically
👥 Group appears automatically
🔁 Group membership is correct

If not, check:

Provisioning logs in Entra

SCIM token validity

Attribute mappings

If user is assigned to the app

🧪 Lab Completion Checklist
Item	Status
SCIM Token created in AWS	✔
SCIM endpoint tested in Entra	✔
Automatic Provisioning enabled	✔
User + Group assigned in Entra	✔
Provision on Demand successful	✔
Identity visible in AWS Identity Center	✔

Congratulations — your environments now support Zero Trust Identity Lifecycle Automation.

🔗 Next Lab →
Lab 04 — Permission Sets & Enterprise RBAC

👉 ./04-permission-sets.md

🔙 Back to Lab 02

👉 ./02-entra-enterprise-app.md

<div align="center">

© 2025 SecureTheCloud.dev — All Rights Reserved
Zero Trust • Multi-Cloud • Enterprise Architecture

</div>
