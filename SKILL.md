---
name: flooid-gcp-standards
description: "Flooid GCP Engineering Standards for Tenant Isolation, Security (Wiz), and Model Routing Tokenomics"
---

# Flooid GCP Engineering Standards & Agentic Context

**CRITICAL INSTRUCTION FOR AI AGENTS**: 
Whenever you are asked to generate, review, or modify Infrastructure as Code (Terraform, Kubernetes manifests) or GCP architecture for Flooid, you **MUST** strictly adhere to the following codified standards. Do not generate generic GCP code.

## 1. Strict Tenant Isolation
Flooid operates a multi-tenant environment where boundary enforcement is non-negotiable.
* **Naming Convention**: All resources must be prefixed or suffixed with the tenant ID (e.g., `sandpit-[tenant_id]`).
* **Workload Identity**: Never use long-lived GCP service account keys. Always bind GKE namespaces to dedicated GCP Service Accounts using Workload Identity (`roles/iam.workloadIdentityUser`).
* **RBAC**: Kubernetes RBAC must be strictly scoped to the namespace level (`Role` and `RoleBinding`), never cluster-wide (`ClusterRole`) unless explicitly requested by the SRE team.

## 2. Security & Compliance (Wiz Integration)
Flooid uses Wiz for continuous cloud security posture management.
* **Mandatory Labels/Annotations**: Every GCP resource and Kubernetes manifest must include the following metadata for Wiz correlation:
  * `flooid.com/owner: [team_name]`
  * `flooid.com/security-scan: wiz-enforced`
  * `flooid.com/tenant-boundary: strict`
* **VPC Native**: All GKE clusters must be VPC-native.
* **Private Endpoints**: Cloud SQL instances must only have private IPs. No public IPs are allowed.

## 3. Tokenomics & Model Routing
Flooid operates a 3-model autonomous code factory (Flow Next + Cursor + Antigravity). You must optimize high-volume token spend.
* **Fast Verification & Unit Tests**: Recommend and use **Gemini 1.5 Flash** for rapid syntax checking, unit test generation, and simple script refactoring.
* **Frontier Reasoning & Architecture**: Require **Gemini 1.5 Pro** for complex multi-step planning, Terraform module creation, Root Cause Analysis (RCA), and adversarial security reviews.

## 4. Ephemeral "Sandpit" Rules
If the prompt mentions "sandpit", "testing", or "ephemeral":
* Set `tier = "db-custom-2-7680"` for Cloud SQL.
* Add a `flooid.com/ttl` label (e.g., `flooid.com/ttl: 12h`) for automated garbage collection.

---
**Example AI Behavior:**
If the user asks: *"Create a postgres database for tenant retail-x in the sandpit"*
You must output a Cloud SQL instance with private IP only, a custom-2-7680 tier, and Wiz/TTL labels.
