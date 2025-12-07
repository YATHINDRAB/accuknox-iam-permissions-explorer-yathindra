# Wireframes — IAM Permissions Explorer  
AccuKnox PM Assignment  
Candidate: **Yathindra Bolloju**

---

## 🔗 Figma Prototype Link
Your Figma design (3 screens):  
**https://www.figma.com/proto/BAP2xcnbxMjTZ8RSdvSLWG/Screen-1-%E2%80%94-Dashboard?node-id=0-1&t=kGzaYJueitcHXKSu-1**

*(Evaluator can navigate between frames using Figma arrows.)*

---

# 📌 Overview
Below are **text-based wireframes** describing the layout and interaction for the 3 core screens.  
These match the visual design created in the Figma link above.

Each screen includes:
- Layout structure  
- Component description  
- Notes / Annotations for evaluators  

---

# 🟦 **SCREEN 1 — IAM Overview Dashboard**

```
+-------------------------------------------------------------+
| IAM Permissions Explorer                 [Search]   [User]  |
+-------------------------------------------------------------+

Account Selector: [All Accounts ▼]  
Time Window: [Last 90 days ▼]

KPI Cards:
 [ Total Principals: 512 ]
 [ Risky Principals: 42 ]
 [ Wildcard Roles: 8 ]

Section: Top Risk Drivers (clickable)
 --------------------------------------------------------------
 | Role Name       | Risk Score | Last Used | Dangerous Perms |
 --------------------------------------------------------------
 | BackupAdmin     | 87         | 400 days  | iam:*, s3:*     |
 | AnalyticsRole   | 73         | 120 days  | ec2:*           |
 --------------------------------------------------------------

Right Panel Filters:
 - Risk Level: Critical / High / Medium / Low
 - Last Used: <30d / 30–90d / >90d / Never
 - Principal Type: Role / User / Service Account
```

### Notes:
- KPI cards act as filters → clicking opens Explorer with filters applied.  
- “Top Risk Drivers” highlights the most risky IAM principals.  
- Right-side filters match cloud security dashboard standards.

---

# 🟦 **SCREEN 2 — Permissions Risk Explorer**

```
+-------------------------------------------------------------+
| Permissions Risk Explorer             [Filters ▾] [Search]  |
+-------------------------------------------------------------+

Left Sidebar Filters:
 - Account Selector
 - Risk: Critical / High / Medium / Low
 - Policy Type: Inline / Attached
 - Last Used: <30d / 30–90d / >90d / Never

Main Table:
 ------------------------------------------------------------------------------
 | Principal         | Type | Risk | Last Used | Permissions | Top Risks     |
 ------------------------------------------------------------------------------
 | BackupAdmin       | Role | 87   | 400 days  | 45          | iam:*         |
 | DataEngineerRole  | Role | 63   | 120 days  | 23          | s3:*          |
 ------------------------------------------------------------------------------

Right Detail Panel (appears when a row is selected):
 - Full policy JSON (collapsible)
 - Last-used activity timeline (CloudTrail-derived)
 - Dangerous permissions overview
 - “Suggested Fix” button
 - “Export Audit Report” button
```

### Notes:
- Table supports scanning, sorting, filtering.  
- Right detail panel supports investigation workflow.  
- Risk score uses wildcard, admin actions, and last-used data.

---

# 🟦 **SCREEN 3 — Recommended Fixes & Patch Preview**

```
+-----------------------------------------------------------+
| Recommended Fixes for: BackupAdmin                        |
+-----------------------------------------------------------+

High-Priority Findings:
 - Contains wildcard permissions: iam:*, s3:*, ec2:*  
 - Unused permissions for 400+ days  
 - Inline policy increases operational risk  

Suggested Remediation Actions:
 1) Remove unused permissions  
 2) Replace wildcard actions with scoped permissions  
 3) Convert inline policy → managed policy  

Terraform Patch Preview (Read-only):
 -----------------------------------------------------------
 resource "aws_iam_policy" "backupadmin_least_privilege" {
   name = "backupadmin_least_privilege"
   ...
 }
 -----------------------------------------------------------

Buttons:
 [Download Patch]   [Export Audit Report]   [Acknowledge]
```

### Notes:
- Patch preview gives transparency and trust before making changes.  
- Exported reports assist with audits (SOC2, PCI-DSS).  
- Actions follow least-privilege best practices.

---

# 📝 Additional Notes for Evaluators

- Wireframes intentionally keep a **minimalistic** and **functional** style.  
- The 3-screen flow shows a realistic IAM investigation workflow:  
  **Dashboard → Explorer → Fixes**  
- Design aligns with cloud security platforms used by IAM engineers and SecOps teams.

---


