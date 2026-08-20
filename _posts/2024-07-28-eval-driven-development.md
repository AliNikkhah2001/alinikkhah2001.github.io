---
layout: post
title: "Eval-Driven Development for LLMs: TDD for the Generative Era"
date: 2024-07-28
author: Alinikkhah
categories: [loss.backward, AI, Evals, Testing, Development]
tags: [Evals, TDD, Testing, LLM, Development, Quality]
excerpt: "Applying Test-Driven Development principles to LLM applications — write evals first, build prompts second."
---

# Eval-Driven Development for LLMs: TDD for the Generative Era

## The Problem

Traditional software engineering has **Test-Driven Development (TDD)**:
1. Write a failing test
2. Write code to pass
3. Refactor

LLM development often skips the "test first" step:
1. Write a prompt
2. Try it a few times
3. "Looks good!" → Ship
3 weeks later: "Why is the bot hallucinating in production?"

## What is Eval-Driven Development (EDD)?

**EDD = Write evals first, build prompts/pipelines second.**

```
Traditional:    Prompt → "Looks good" → Ship → 💥
EDD:            Evals → Prompt → Evaluate → Iterate → Ship → ✅
```

## Why EDD Matters

| Without EDD | With EDD |
|-------------|----------|
| "Vibes-based" quality | Measurable quality |
| Surprise regressions | Caught in CI |
| "It works on my machine" | Reproducible quality |
| "Prompt engineering" | Prompt engineering science |

---

## The EDD Workflow

```
1. DEFINE → What does "good" look like?
2. MEASURE → How do we quantify "good"?
3. BASELINE → What does current system do?
4. ITERATE → Improve prompt/pipeline
5. REGRESS → CI catches regressions
```

---

## Step 1: Define Success Criteria

Before writing any prompt, define what "correct" means:

```python
# Example: SQL generation task
SUCCESS_CRITERIA = {
    "syntax_valid": True,           # Valid SQL syntax
    "executes": True,               # Runs without error
    "correct_columns": True,        # Uses correct column names
    "correct_joins": True,          # Proper JOIN logic
    "no_hallucination": True,       # No invented tables/columns
    "performance": "< 100ms",       # Latency budget
}
```

---

## Step 2: Build Evaluation Suite

### Types of Evaluations

```python
class LLMEvaluator:
    def __init__(self):
        self.evaluators = {
            "exact_match": self.exact_match,
            "semantic_similarity": self.semantic_similarity,
            "factual_accuracy": self.factual_accuracy,
            "format_compliance": self.format_compliance,
            "safety": self.safety_check,
            "latency": self.latency_check,
        }
    
    def evaluate(self, prediction, reference, context=None):
        results = {}
        for name, evaluator in self.evaluators.items():
            results[name] = evaluator(prediction, reference, context)
        return results
```

### Evaluation Types

| Evaluator | Use Case | Implementation |
|-----------|----------|----------------|
| **Exact Match** | Deterministic outputs | String equality |
| **Semantic Similarity** | Open-ended generation | Embedding cosine sim |
| **Factual Accuracy** | Factual QA | Fact-checking model/API |
| **Format Compliance** | JSON, SQL, Code | Schema validation |
| **Safety** | Toxicity, PII, hallucination | Safety classifier |
| **Latency** | Performance | Wall-clock time |

---

## Step 3: Build Test Cases

### Test Case Structure

```python
TEST_CASES = [
    {
        "id": "sql_basic_select",
        "input": "Show all users from California",
        "context": {"schema": USERS_SCHEMA},
        "expected": {
            "sql": "SELECT * FROM users WHERE state = 'CA'",
            "columns": ["id", "name", "email", "state"],
        },
        "tags": ["basic", "select", "where"],
    },
    {
        "id": "sql_complex_join",
        "input": "Show orders with customer names for 2024",
        "context": {"schema": ORDERS_SCHEMA},
        "expected": {
            "sql": "SELECT o.*, c.name FROM orders o JOIN customers c ON o.customer_id = c.id WHERE o.year = 2024",
            "tables": ["orders", "customers"],
        },
        "tags": ["join", "filter", "date"],
    },
    # Edge cases
    {
        "id": "sql_ambiguous_column",
        "input": "Show user id and name",
        "context": {"schema": AMBIGUOUS_SCHEMA},  # Both tables have 'id'
        "expected": {"error": "ambiguous_column"},
        "tags": ["edge_case", "ambiguity"],
    },
]
```

---

## Step 4: Evaluation Pipeline

```python
class EDDPipeline:
    def __init__(self, model, evaluator, test_cases):
        self.model = model
        self.evaluator = evaluator
        self.test_cases = test_cases
    
    def run_evaluation(self, prompt_template):
        results = []
        for case in self.test_cases:
            prompt = prompt_template.format(**case["input"])
            prediction = self.model.generate(prompt)
            eval_result = self.evaluator.evaluate(
                prediction, 
                case["expected"], 
                case.get("context")
            )
            results.append({
                "case_id": case["id"],
                "tags": case.get("tags", []),
                "passed": all(eval_result.values()),
                "scores": eval_result,
                "prediction": prediction,
            })
        return results
    
    def summary(self, results):
        total = len(results)
        passed = sum(1 for r in results if r["passed"])
        by_tag = defaultdict(list)
        for r in results:
            for tag in r["tags"]:
                by_tag[tag].append(r["passed"])
        
        return {
            "overall_pass_rate": passed / len(results),
            "by_tag": {tag: sum(v)/len(v) for tag, v in by_tag.items()},
            "failed_cases": [r for r in results if not r["passed"]],
        }
```

---

## Step 5: CI Integration

### GitHub Actions Workflow

```yaml
# .github/workflows/llm-evals.yml
name: LLM Evaluations

on:
  push:
    paths:
      - 'prompts/**'
      - 'evals/**'
  pull_request:

jobs:
  evaluate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      
      - name: Install dependencies
        run: pip install -r evals/requirements.txt
      
      - name: Run evaluations
        run: python evals/run_evals.py --prompts prompts/
        env:
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
          OPENROUTER_API_KEY: ${{ secrets.OPENROUTER_API_KEY }}
      
      - name: Upload results
        uses: actions/upload-artifact@v4
        with:
          name: eval-results
          path: eval_results/
      
      - name: Comment PR with results
        if: github.event_name == 'pull_request'
        uses: actions/github-script@v7
        with:
          script: |
            // Post evaluation summary as PR comment
```

---

## Prompt Versioning

```bash
prompts/
├── v1_basic_prompt.txt
├── v2_added_examples.txt
├── v3_chain_of_thought.txt
├── v4_few_shot_cot.txt
└── v5_self_correction.txt
```

Each version evaluated against the same test suite:

| Version | Pass Rate | Latency | Cost |
|---------|-----------|---------|------|
| v1_basic | 45% | 1.2s | $0.02 |
| v2_examples | 62% | 1.5s | $0.03 |
| v3_cot | 78% | 2.1s | $0.05 |
| v4_few_shot | 85% | 2.8s | $0.07 |
| v5_self_correct | **91%** | 3.5s | $0.12 |

---

## Regression Detection

```python
def check_regression(current_results, baseline_results, threshold=0.05):
    """Alert if any metric drops more than threshold"""
    regressions = []
    for metric in ["pass_rate", "latency", "cost"]:
        current = current_results[metric]
        baseline = baseline_results[metric]
        if current < baseline - threshold:
            regressions.append({
                "metric": metric,
                "baseline": baseline,
                "current": current,
                "delta": current - baseline,
            })
    return regressions
```

---

## Real-World Example: SQL Generator

### Before EDD
- Prompt: "Write SQL for the user's question"
- "Seemed to work" in manual testing
- Production: 40% error rate, hallucinated columns

### After EDD
1. **Defined** 50 test cases covering joins, filters, edge cases
2. **Built** evaluator with syntax check, execution, semantic similarity
3. **Baseline**: v1 prompt → 34% pass rate
4. **Iterated** through 6 prompt versions
4. **Result**: v6 → 94% pass rate, caught in CI

---

## Tools & Frameworks

| Tool | Purpose |
|------|---------|
| **LangSmith** | Tracing, evaluation, monitoring |
| **LangChain Evals** | Built-in evaluators |
| **Ragas** | RAG-specific evals (faithfulness, relevance) |
| **DeepEval** | Comprehensive LLM eval framework |
| **PromptFoo** | CLI-based prompt testing |
| **PromptLayer** | Prompt versioning + evals |

---

## EDD Checklist

- [ ] Success criteria defined for each task
- [ ] Test cases cover happy path + edge cases
- [ ] Evaluators cover: correctness, format, safety, latency
- [ ] Baseline established for current system
- [ ] CI runs evals on every prompt change
- [ ] Regression alerts configured
- [ ] Prompt versions tracked and evaluated
- [ ] Human review for failed cases
- [ ] Regular eval suite maintenance

---

## The EDD Mindset

> *"If you can't measure it, you can't improve it."*

**EDD transforms prompt engineering from art to engineering discipline.**

Start small: pick one task, write 5 eval cases, run them against your current prompt. Watch the numbers. Iterate.

---

> *"In God we trust; all others must bring data."* — W. Edwards Deming

---

*Part of the [loss.backward](/loss-backward/) series — production lessons from the trenches of ML systems.*