# Secure Container API on Azure Container Apps

## Goal
Deploy a secure API layer running in Azure Container Apps, connected to a database via views/tables and exposing authenticated endpoints.

## What I built
- Containerised API using Microsoft Data API Builder (DAB)
- Connected DAB to a database using views for complex queries
- Configured API endpoints
- Enforced authentication on endpoints

## Architecture (high level)
Client -> Auth -> Azure Container Apps (DAB API) -> Database Views -> Database

## Security
- Auth required on endpoints (Entra ID Authentication)
- Secrets stored securely (TBD: Key Vault / App secrets / managed identity)

## Key implementation decisions
- Used DB Views to keep API logic clean and reusable
- Used ACA for scalable container hosting with minimal ops

## Challenges + Fixes
- [Add your real issues and how you solved them]

## Proof
- Screenshot(s): `/assets/images`
- Diagram(s): `/assets/diagrams`
- Demo: [optional link]

## Next upgrades
- Add IaC (Bicep/Terraform)
- Add CI/CD deployment
- Add monitoring + alerts
