# Secure API Layer on Azure Container Apps (Data API Builder + Entra Auth)

## Problem
A business application needed a secure API layer to expose database-backed data with authentication and controlled access.

## Constraints
- Must support secure authentication (identity-first)
- Must avoid embedding query complexity in app code
- Must be deployable and maintainable with minimal ops overhead

## What I built
- Containerized API using Microsoft Data API Builder (DAB)
- Hosted on Azure Container Apps
- Connected to a database using Views for complex query logic
- Exposed REST endpoints configured in DAB
- Enforced authentication required on endpoints using Microsoft Entra ID

## Architecture (high level)
Client -> Entra ID Auth -> Azure Container Apps (DAB API) -> Database Views -> Database

## Key Technical Decisions
Decision 1 - Azure COntainer Apps vs AKS
- Chosen for reduced ops overhead + scaling features without full Kubernetes management
Decision 2 - Database Viwes
- Used views to keep API logic clean, reusable, and consistent
- Reduced application-side query complexity
Decision 3 - Entra authentication
- Protected endpoints to enforce secure access
- Avoided exposing data anonymously

## Challenges + how I solved them
- Auth misconfiguration / unauthorized errors
  - Resolved by validating token audience/issuer + ensuring API required auth per endpoint config
- Database permission/access issues
  - Resolved by aligning DB role permissions and validating connection string / firewall rules (generic)
- Endpoint mapping not returning expected data
  - Resolved by adjusting DAB entity mappings and validating view output
 
## Security
- Authentication enforced on all endpoints
- Key Vault to be implemented
- Principle of least privilege applied where possible

## Results / Impact
- Reduced development effort by centralizing query logic in DB views
- Delivered a scalable API layer with minimal operational overhead
- Improved security posture by enforcing authentication on endpoints

## Proof
- Screenshot(s): `/assets/images`
- Diagram(s): `/assets/diagrams`

## Next upgrades
- Add Key Vault
- Add IaC (Bicep/Terraform)
- Add CI/CD deployment
- Add monitoring + alerts
