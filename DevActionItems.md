# Development Action Items (Engineering Plan)

---

## 1. Data Ingestion
- Pull IAM metadata: list-roles, list-policies, get-policy-version  
- Map principals → attached/inline policies  
- Store policy statements in normalized form  
- CloudTrail integration for last-used inference  

---

## 2. Risk Engine (Backend)
Weighted scoring based on:
- Wildcards (`*:*`)  
- Admin permissions (`iam:*`, `ec2:*`, `s3:*`)  
- Sensitive permissions (privilege escalation patterns)  
- Last-used timestamps (>90 days → high risk)  

Score = 0–100

---

## 3. API Endpoints
- `GET /principals?filters`  
- `GET /principals/{id}`  
- `GET /principals/{id}/policy-diff`  
- `POST /principals/{id}/export`  

---

## 4. Remediation Engine
- Identify unused permissions  
- Generate delta least-privilege policy  
- Terraform snippet generator  
- Inline → managed policy recommendation  

---

## 5. UI Tasks
- Dashboard KPIs component  
- Explorer table + filters  
- Right-side details panel  
- Fixes page with patch preview  

---

## 6. Non-Functional
- Must scale to 50–100 cloud accounts  
- RBAC for sensitive IAM data  
- Audit logging  

### Example API endpoints (quick reference)
- `GET /principals?account=<id>&risk=<level>&last_used=<window>`
  - Returns list of principals matching filters (supports pagination).
- `GET /principals/{principal_id}`
  - Returns full policy detail, risk breakdown, last-used timeline.
- `GET /principals/{principal_id}/policy-diff`
  - Returns suggested least-privilege policy (delta) and Terraform patch snippet.
- `POST /principals/{principal_id}/export`
  - Triggers export of audit report (PDF/CSV).

