# Amboras Plan

## What This Repo Is

This is the **strategic planning and research repository** for **Amboras** — an AI-native e-commerce platform built to compete with Shopify.

It is not a codebase. It is a living research vault: competitor analysis, merchant pain points, feature ideas, architecture decisions, and product strategy. Everything here feeds into what Amboras becomes.

---

## What Is Amboras

Amboras is a full shop system built AI-native from day one.

**The core thesis:**
> Shopify gives you the tools but doesn't guarantee your sales or help you make sales. All tools are slow and not AI-compatible. For everything, you need a secondary app — even just to write a product description.

Amboras fixes this by being outcome-focused, not tool-focused. It doesn't just give merchants a storefront — it actively helps them sell. AI is not a plugin. It is the foundation.

---

## Context

Amboras is built by the team behind **Ecomcoder** (ecomcoder.com) — an AI Shopify theme editor used by 400+ stores. The founders (Amin and Imad Mokadem) scaled their own DTC brand to 6 figures/month on Shopify and lived every pain point firsthand.

Ecomcoder proved that merchants desperately want AI in their workflow. Amboras is the full vision: not just AI for theme editing, but AI woven into every part of running a store.

---

## Repo Structure

```
negative-reviews/       # Raw merchant complaints — Shopify, apps, competitors
plan/                   # The actual plan — features, architecture, positioning, roadmap
  ├── INDEX.md          # Master index of all plan documents with status
  ├── features/         # What Amboras does
  ├── architecture/     # How it's built
  ├── positioning/      # Who it's for and how we talk about it
  └── roadmap/          # Phases and milestones
```

---

## How We Work

### General
- This is research and strategy, not production code — no over-engineering
- Every file should be directly useful for building Amboras, no fluff
- One topic per file, named descriptively
- Keep it startup-speed: rough and useful beats polished and slow

### Adding to the Plan
- New ideas go in `plan/features/`, `plan/architecture/`, `plan/positioning/`, or `plan/roadmap/`
- Every new file gets a row in `plan/INDEX.md` with a status label
- Status flow: `idea → validated → decided → in-progress`
- Don't mark something `decided` until it's backed by research or a deliberate team call

### Negative Reviews
- Drop raw reviews into `negative-reviews/` in any format (text, screenshots, links)
- Update `negative-reviews/NOTES.md` with patterns as they emerge
- Every pattern should map to a specific Amboras feature or positioning angle

### Claude's Role
- Read `plan/INDEX.md` to get oriented at the start of any session
- When analyzing reviews or research, always tie findings back to the core thesis
- Flag patterns that validate or challenge the Amboras vision
- Suggest where new information belongs in the folder structure
- Ask before creating new top-level folders
