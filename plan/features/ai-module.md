# AI Module

## What & Why

Every page in the Amboras admin has AI built in. This is not a feature bolted on — it is the core interaction model. Merchants manage their entire store through AI conversation.

The AI module is one unified system with two modes:
1. **Full-page AI** — A dedicated "AI" page at the top of the admin sidebar (above Orders, Analytics, everything). Full chat interface like ChatGPT/Claude. The merchant's primary way to interact with Amboras.
2. **Contextual AI** — A compact chat input on every other admin page (Orders, Customers, Products, etc.) pre-configured for that page's domain.

There is **one AI module** that powers everything. Every AI instance has exactly two things that define its behavior:
- **System prompt** — assistant instructions, sent with every message
- **CLAUDE.md** — context about what the AI can do on that page

The module itself (chat UI, API calls, message handling) is always the same. Only the system prompt and CLAUDE.md change per page.

---

## Part 1: UI/UX

### Full-Page AI (the "AI" sidebar item)
- Top item in the left sidebar — above Orders, Analytics, everything
- Full-screen chat interface: input field, scrollable message history, like ChatGPT.com or Claude.com
- Has its own system prompt + CLAUDE.md scoped to "manage the entire store"
- This is the most powerful instance — it can do anything across the platform
- **Chat history sidebar** — list of all previous conversations, clickable to reopen (like ChatGPT's left panel)
- Tool usage (actions the AI took) displayed inline in the chat — merchant can see what the AI did

### Contextual AI (per-page chat)
- Every admin page (Orders, Customers, Products, Analytics, etc.) has a small text input
- Positioned above the page content
- Has a page-specific system prompt + CLAUDE.md (e.g., Orders AI only knows about orders)
- Same chat component, just scoped differently
- Can start simpler: short conversation history, but still persisted

### Shared UI behavior
- One shared chat component, reusable everywhere
- System prompt and CLAUDE.md loaded per-page via config
- Adding AI to a new page = write a system prompt, write a CLAUDE.md, drop in the component

---

## Part 2: Architecture

### Database schema
Everything the AI does must be stored in the database:
- **Conversations** — each chat session (who, when, which page/context)
- **Messages** — every message in a conversation (role: user/assistant/system, content, timestamps)
- **Tool calls** — every tool the AI invoked (tool name, input, output, status, duration)
- **System prompts** — the system prompt used for each conversation (versioned)
- **CLAUDE.md files** — the CLAUDE.md content used (versioned)
- **Token usage** — input/output tokens per message for cost tracking

This is the single source of truth. The chat UI reads from this database. The AI API writes to this database.

### Modular tool system
- Tools are registered in the database — each tool has a name, description, schema, and enabled/disabled flag
- When a new tool or MCP is added, it gets registered once and is immediately available to any AI instance
- Tool calls are logged with full input/output so we can trace exactly what the AI did
- Tool availability can be scoped per page (e.g., Orders AI only gets order-related tools)

### Lunary compatibility
- The database schema is designed so we can pipe everything into Lunary for monitoring and debugging
- Every conversation, message, tool call, and token usage is stored in a format that maps to Lunary's data model
- This gives us: conversation replay, tool call inspection, cost tracking, latency monitoring, error tracing

### API layer
- One AI API endpoint that accepts: message, conversation_id, context (which page)
- The API loads the correct system prompt + CLAUDE.md based on context
- Streams the response back to the frontend
- Persists everything (message in, message out, tool calls) to the database before/after the Claude API call

### Flow
```
User types message
    → Frontend sends: { message, conversation_id, context }
    → API looks up system prompt + CLAUDE.md for that context
    → API loads available tools for that context
    → API saves user message to DB
    → API calls Claude with: system prompt + CLAUDE.md + conversation history + tools
    → Claude responds (possibly with tool calls)
    → API saves tool calls + results to DB
    → API saves assistant message to DB
    → API streams response back to frontend
```

---

## Conditions & Requirements to Consider

- The AI module is **standalone** — completely decoupled from the AI Service in the system architecture
- System prompts and CLAUDE.md files should be version-controlled (git) and also stored in DB per conversation for replay
- Model selection (Claude Sonnet, Opus, Haiku) should be configurable per context
- Must handle streaming responses for good UX
- Database must support the full audit trail — we never lose a prompt, response, or tool call
- Adding a new tool should be: register it in the DB, add it to the relevant page configs, done
