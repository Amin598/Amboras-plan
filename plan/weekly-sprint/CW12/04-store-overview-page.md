# PRD: Store Overview Page

## 1. What & Why

The first thing a merchant sees after logging in — a dashboard showing all their stores. This is the hub where they pick which store to manage, see store status at a glance, and create new stores. Without this, merchants can't navigate to their store.

## 2. What It Must Do

- Dashboard page at admin.amboras.com showing all stores belonging to the logged-in user
- Fetch all stores related to user from orchestrator DB (Supabase)
- Each store card shows: store name, domain, status (live/staging/down), preview thumbnail
- "Create new store" button → triggers store provisioning flow (PRD #02)
- Click into a store → opens the Medusa admin for that specific store
- Handle edge cases: no stores yet (empty state with CTA), store machine down (show status)

## 3. Conditions & Requirements

- Depends on PRD #01 (orchestrator platform) being live
- Depends on PRD #02 (store provisioning) for the create store flow
- Store status must be real-time or near real-time (poll or websocket)
- Preview thumbnails: either screenshot service or static placeholder for MVP
- Must work on mobile (responsive)
