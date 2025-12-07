# Product Requirements Document (PRD)
## IAM Permissions Explorer — AccuKnox PM Assignment

---

## 1. Problem Statement
Cloud environments accumulate excessive, unused, and overly broad IAM permissions.  
This creates **privilege creep**, compliance violations, and increases the attack surface.  
Security teams lack a **simple, centralized view** to:

- Identify risky IAM roles/users  
- Understand which permissions are unused  
- Prioritize remediation steps  
- Move toward least-privilege access  

---

## 2. Goal
Create a simple, practical IAM Permissions Explorer that:

- Detects excessive or unused permissions  
- Scores and prioritizes risky IAM principals  
- Provides clear, actionable remediation guidance  
- Supports multi-account environments  

---

## 3. Target Users
See detailed persona in `UserPersona.md`.

---

## 4. MVP Features

### **A) Overview Dashboard**
- Total principals  
- Count of risky principals  
- Roles with wildcard (`*:*`) permissions  
- Top 5 risk drivers  
- Quick filters (risk level, last-used windows)

---

### **B) Permissions Risk Explorer**
- Table view of IAM principals (roles/users/service accounts)  
- Columns: Principal, Type, Risk Score, Last Used, Permissions Count  
- Expandable row → show policy list + top dangerous permissions  
- Filters: Account, region, risk score, last used, policy type  
- Search by principal name  

---

### **C) Recommended Fixes & Patch Preview**
- Suggested least-privilege policy  
- List of unused permissions  
- Wildcard permission replacement suggestions  
- Terraform patch snippet preview  
- Export audit report  

---

## 5. Prioritization (RICE summary)

| Feature | R | I | C | E | Score |
|--------|---|---|---|---|--------|
| Risk scoring engine | 10 | 9 | 7 | 8 | **720** |
| Last-used detection | 9 | 8 | 6 | 7 | **504** |
| Explorer UI + Filters | 8 | 7 | 6 | 8 | **448** |
| Terraform remediation generator | 7 | 6 | 4 | 5 | **210** |

---

## 6. Success Metrics
- Reduce number of risky principals by **30%** in 90 days  
- Detect wildcard roles with **100% accuracy**  
- Time-to-remediate risky roles drops by **50%**  
- Explorer adoption: **60%** of security team uses weekly  
- Exported audit reports per month  

---

## 7. Assumptions
- IAM policy & CloudTrail data is available  
- Organization uses AWS initially; GCP/Azure future  
- Users have permission to view IAM metadata  

---

## 8. Non-Functional Requirements
- Scalable across 50–100+ cloud accounts  
- Role-based access to Explorer  
- API-based back end for real-time updates  


