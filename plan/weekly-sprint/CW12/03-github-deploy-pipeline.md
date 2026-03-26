# PRD: GitHub Deploy Pipeline

## 1. What & Why

Every store's code lives in a GitHub repo, and deployments happen via git push. This gives us version control, rollback capability, and a clean deployment flow. The template repo is the base that every new store forks from — ensuring consistency and making updates easy to propagate.

## 2. What It Must Do

- **Template repo:** `amboras-stores/store-template` containing base Medusa + Next.js storefront + AI service
- **Per-store repos:** on store creation, fork template into `amboras-stores/store-{id}`
- **Branch strategy:** `staging` (auto-deploy) → `main` (manual deploy to production)
- **GitHub webhooks:** push to branch → webhook hits orchestrator API → triggers deployment on the store's Fly.io machine
- **Deploy flow:** git push → webhook → orchestrator queues job → Fly.io machine pulls latest → build → health check → live
- Orchestrator tracks: current deployed commit per store, deployment history, deployment status

## 3. Conditions & Requirements

- GitHub organization `amboras-stores` needs to be created
- GitHub App or OAuth token for creating repos and managing webhooks programmatically
- Webhook secret for secure communication
- Deploy worker needs to handle concurrent deployments (queue, not parallel per store)
- Template repo must be kept up to date — changes to template should be easy to merge into existing store repos
- Consider GitHub Actions vs custom deploy worker for the build step
