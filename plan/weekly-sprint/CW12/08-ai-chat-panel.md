# PRD: AI Chat Panel

## 1. What & Why

The core differentiator of Amboras — an AI chat panel built into the Medusa admin where merchants can talk to AI to manage their store. Create products, generate descriptions, get sales advice, modify the storefront — all through conversation. This is what makes Amboras AI-native, not just another shop system.

Built on top of the Ecomcoder experience — chat-first, action-oriented.

## 2. What It Must Do

- Chat panel integrated into the Medusa admin UI (admin.amboras.com) — always accessible, side panel or overlay
- Text input, message history, AI responses with rich formatting
- AI service (port 8000 on store machine) handles chat requests
- AI connects to Claude API for intelligence
- AI has access to Medusa API — can read/write:
  - Products (create, edit, delete)
  - Orders (view, update status)
  - Customers (view)
  - Store settings
- AI responses can include actions: "I created product X" with a link to view it
- Conversation history persisted per store

## 3. Conditions & Requirements

- Depends on PRD #02 (store machine with AI service running on port 8000)
- Claude API key management: per-platform key (Amboras pays), not per-merchant
- AI service needs authenticated access to the store's Medusa API
- Consider rate limiting AI usage per merchant (tied to plan/billing later)
- Chat UI should be lightweight — don't slow down the admin
- Design should match Amboras branding
- Start simple: text chat only. Image generation, storefront editing come later.
