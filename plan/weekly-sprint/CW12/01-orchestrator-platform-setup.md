# PRD: Orchestrator Platform Setup

## 1. What & Why

Set up the central Amboras platform that all merchants interact with. This is the Fly.io server running the backend API (NestJS), connected to Supabase for user/store data, with amboras.com serving the landing page, pricing, and login/signup. After login, merchants get redirected to admin.amboras.com.

This is the foundation — nothing else works without it. Every other PRD depends on this being live.

## 2. What It Must Do

- Fly.io server running NestJS backend API
- Supabase as orchestrator DB with tables: users, stores, deployments
- User auth (OAuth — Google, email/password at minimum)
- amboras.com serves: landing page, pricing page, login/signup
- After successful login → redirect to admin.amboras.com
- API endpoints: create user, get user, create store, list stores, get store
- Environment variables and secrets management

## 3. Conditions & Requirements

- Supabase project needs to be created and configured
- Fly.io account and app need to be provisioned
- Auth flow must be secure — JWT tokens, refresh tokens
- DB schema must support multi-store per user from day one
- Consider rate limiting on auth endpoints
- CORS setup for amboras.com ↔ admin.amboras.com ↔ API communication
