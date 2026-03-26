# PRD: Store Machine Provisioning

## 1. What & Why

Every Amboras store runs on its own Fly.io machine with 3 separate processes (Option B from Architecture-mvp-v1). When a merchant creates a store, the orchestrator automatically spins up a machine, seeds the database, and makes the store live. This is the core infrastructure that makes Amboras a platform — each merchant gets their own isolated environment.

## 2. What It Must Do

- On store creation: orchestrator calls Fly.io Machines API → creates a new machine
- Machine runs 3 processes via pm2 or supervisor:
  - Process 1: Medusa backend (port 9000) — shop engine API
  - Process 2: Next.js storefront (port 3000) — customer-facing store
  - Process 3: AI service (port 8000) — Claude API, chat, product generation
- Each store connects to Supabase for persistent data (products, orders, customers, carts)
- Redis runs natively with Medusa (session cache, job queues)
- Health check endpoint — orchestrator verifies machine is running
- Auto-rollback if health check fails after deployment
- Store record saved in orchestrator DB with: store ID, machine ID, status, owner user ID

## 3. Conditions & Requirements

- Fly.io Machines API access and billing set up
- Docker image or build script that sets up all 3 processes on a single machine
- Supabase must support per-store database isolation (separate schemas or separate projects — decide which)
- Machine startup time should be under 60 seconds
- Need a strategy for machine auto-suspend (staging) vs always-on (production)
- Consider machine specs: how much RAM/CPU per store machine
