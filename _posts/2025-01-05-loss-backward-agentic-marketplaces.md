---
layout: post
title: "Loss.backward #01 — Agentic Marketplaces in Production"
categories:
  - loss.backward
<<<<<<< HEAD
tags:
  - agentic rag
  - marketplaces
  - mlops
  - production systems
=======
>>>>>>> main
excerpt: >-
  Lessons from designing retrieval-augmented, multi-agent control planes that govern millions of e-commerce
  listings while meeting audit and latency constraints.
---

Shipping agentic ML into a marketplace is less about heroic prompts and more about the rigor of the
pipeline surrounding them. Over the past year at Digikala we hardened a Retrieval-Augmented Generation
stack that pairs modular control planes (MCPs) with retrieval, evaluation, and alignment services.

Key ingredients that kept the system resilient:

1. **Hybrid retrieval graphs.** Vector stores surface semantic context, but dense keyword indexes still win
   whenever the legal team needs deterministic lookups. Orchestrating both under a single planner reduced
   hallucinations by 31% at launch.
2. **Role-specific agents.** Every agent has a single job—classify, retrieve, redact, or explain—and exports
   a health signal. The orchestration layer only composes agents that are healthy, and automatically falls
   back to deterministic baselines when a role flaps.
3. **Observation-first evaluation.** We log every tool invocation, latency bucket, and regulatory tag. Those
   traces stream into a review board where policy, engineering, and operations inspect drift and ship new
   guardrails weekly.

The essay doubles as a field note for teams that want to scale AI governance without hiring an army of
moderators. I also published the underlying scaffolding as the
[`agentic-commerce-control`](https://github.com/AliNikkhah2001/agentic-commerce-control) repository so you can
bootstrap your own marketplace-ready MCP.
