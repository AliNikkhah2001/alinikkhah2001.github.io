---
layout: post
title: "RAG vs Fine-tuning: When to Use Which (A Decision Framework)"
date: 2024-08-05
author: Alinikkhah
categories: [loss.backward, AI, RAG, Fine-tuning, Architecture]
tags: [RAG, Fine-tuning, LLM, Architecture, Decision Framework]
excerpt: "A practical decision framework for choosing between RAG and fine-tuning based on your use case, data, and constraints."
---

# RAG vs Fine-tuning: When to Use Which (A Decision Framework)

## The Eternal Question

Every team building with LLMs faces this decision: **RAG or Fine-tuning?** The answer is rarely binary — most production systems use both. But knowing *when* to reach for each is crucial.

## Quick Decision Tree

```
START: Do you need the model to know NEW information not in training?
├── NO → Fine-tuning might work (style, format, reasoning patterns)
└── YES → Does the information change frequently?
    ├── YES → RAG (knowledge base updates without retraining)
    └── NO → How much data?
        ├── Small (< 10K docs) → Fine-tuning + RAG hybrid
        ├── Medium (10K-1M) → RAG primary, fine-tune for style
        └── Large (> 1M) → RAG with hierarchical retrieval
```

---

## RAG: Retrieval-Augmented Generation

### When RAG Shines

| Scenario | Why RAG |
|----------|---------|
| **Knowledge changes frequently** | Update docs, not model |
| **Need citations/sources** | Built-in provenance |
| **Large knowledge base** | Scales to millions of docs |
| **Multiple domains** | Separate indexes per domain |
| **Compliance/ audit trails** | Full retrieval trace |
| **Rapid iteration** | Update docs, not retrain |

### RAG Architecture

```
User Query → Embed → Vector Search → Top-K → Rerank → Context → LLM → Answer
                    ↓
            Vector DB (Pinecone, Weaviate, Qdrant, Chroma)
```

### Key RAG Decisions

| Decision | Options | Recommendation |
|----------|---------|----------------|
| **Chunking** | Fixed, semantic, recursive | Semantic (semantic chunking) |
| **Embedding** | OpenAI, Cohere, BGE, E5 | BGE-large-en-v1.5 or E5-large |
| **Retrieval** | Dense, sparse, hybrid | Hybrid (BM25 + dense) |
| **Reranking** | Cross-encoder, LLM | Cross-encoder (bge-reranker) |
| **Context window** | 4K, 8K, 32K, 128K | Fit to model + leave room for generation |

### RAG Failure Modes

| Failure | Symptom | Fix |
|---------|---------|-----|
| **Lost in middle** | Answer ignores middle context | Better chunking, position-aware attention |
| **Hallucination** | Model ignores retrieved context | Stronger system prompt, citations |
| **Irrelevant retrieval** | Wrong docs retrieved | Better embeddings, query expansion |
| **Context overflow** | Context too long | Summarization, hierarchical retrieval |

---

## Fine-tuning: Adapting the Model

### When Fine-tuning Shines

| Scenario | Why Fine-tune |
|----------|---------------|
| **Style/format adaptation** | Consistent output format |
| **Reasoning patterns** | Chain-of-thought, specific logic |
| **Domain vocabulary** | Medical, legal, code terminology |
| **Behavioral alignment** | Safety, tone, refusal patterns |
| **Efficiency** | Smaller model matching larger base |

### Fine-tuning Approaches

| Method | Parameters | Data Needed | Use Case |
|--------|------------|-------------|----------|
| **Full FT** | All params | 10K-1M+ | Full domain adaptation |
| **LoRA** | ~1% params | 1K-100K | Efficient adaptation |
| **QLoRA** | ~1% params (4-bit) | 1K-100K | Memory efficient |
| **Prefix/Prompt Tuning** | ~0.1% params | 100-10K | Light adaptation |

### Fine-tuning Data Requirements

| Quality | Quantity | Result |
|---------|----------|--------|
| High (expert) | 100-1K | Surprising good |
| Medium (synthetic) | 1K-10K | Decent |
| Low (noisy) | 10K+ | Marginal |

**Rule**: 100 high-quality examples > 10,000 noisy ones.

---

## The Hybrid Approach (Recommended)

Most production systems use **RAG + Fine-tuning**:

```
┌─────────────────────────────────────┐
│           User Query                │
└─────────────┬───────────────────────┘
              ↓
┌─────────────────────────────────────┐
│        RAG Retrieval                │
│  (Knowledge, facts, citations)      │
└─────────────┬───────────────────────┘
              ↓
┌─────────────────────────────────────┐
│    Fine-tuned LLM                   │
│  (Style, reasoning, format)         │
└─────────────┬───────────────────────┘
              ↓
┌─────────────────────────────────────┐
│         Final Answer                │
└─────────────────────────────────────┘
```

**Fine-tune for**: Style, tone, reasoning patterns, output format, refusal behavior  
**RAG for**: Factual knowledge, citations, up-to-date info, domain specifics

---

## Decision Matrix

| Factor | Choose RAG | Choose Fine-tuning | Hybrid |
|--------|------------|-------------------|--------|
| Knowledge freshness | Critical | Not needed | Critical |
| Data volume | High | Low-Medium | High |
| Update frequency | Daily/Weekly | Monthly/Quarterly | High |
| Citation needed | Yes | No | Yes |
| Format/style control | Low | High | High |
| Latency budget | Higher OK | Low | Balanced |
| Team expertise | RAG pipelines | ML training | Both |
| Compute budget | Lower | Higher | Higher |

---

## Practical Recommendations by Use Case

| Use Case | Recommendation |
|----------|----------------|
| **Customer Support Bot** | RAG (knowledge base) + FT (tone/policy) |
| **Code Assistant** | RAG (docs/API) + FT (code style) |
| **Legal/Compliance** | RAG (citations critical) + FT (format) |
| **Medical QA** | RAG (citations!) + FT (terminology) |
| **Creative Writing** | FT (style) + Light RAG (facts) |
| **Code Generation** | RAG (API docs) + FT (patterns) |
| **Internal Knowledge Bot** | RAG (internal docs) + Light FT |

---

## Implementation Checklist

### For RAG:
- [ ] Choose embedding model
- [ ] Set up vector DB
- [ ] Design chunking strategy
- [ ] Implement retrieval + reranking
- [ ] Add citation formatting
- [ ] Set up evaluation (hit rate, MRR)
- [ ] Implement monitoring (latency, hit rate)

### For Fine-tuning:
- [ ] Curate high-quality dataset
- [ ] Choose method (LoRA/QLoRA/Full)
- [ ] Set up training infrastructure
- [ ] Define evaluation metrics
- [ ] Run hyperparameter search
- [ ] Validate on holdout set
- [ ] Plan deployment (merge, quantize)

---

## Cost Comparison (Approximate)

| Approach | Setup Cost | Ongoing Cost | Latency |
|----------|------------|--------------|---------|
| RAG Only | $500-5K | $100-5K/mo | Medium |
| FT Only (LoRA) | $1K-10K | $0 (static) | Low |
| Hybrid | $2K-15K | $100-5K/mo | Medium |

---

## Final Recommendation

**Start with RAG**. It's faster to iterate, easier to debug, and handles knowledge updates naturally.

**Add Fine-tuning when**:
- RAG retrieval is good but output format/style is wrong
- You need specific reasoning patterns
- Latency is critical (smaller fine-tuned model)
- You have high-quality training data

**The winning combo**: RAG for knowledge + Fine-tuning for behavior.

---

> *"RAG gives the model a library. Fine-tuning teaches it how to read."* — paraphrased

---

*Part of the [loss.backward](/loss-backward/) series — production lessons from the trenches of ML systems.*