---
name: New Diagnostic Prompt Submission
about: Submit a completely new test prompt scenario to be integrated into the core evaluation suite.
title: '[PROMPT SUBMISSION]: '
labels: ['new-prompt', 'contribution']
assignees: ''
---

## Diagnostic Objective
What specific edge case, failure mode, or cognitive limitation is this prompt designed to uncover in an LLM?

## Proposed Prompt File Name
Following the established repository pattern (e.g., tracking alongside existing files llm-debugger-1.md through llm-debugger-10.md), what is the proposed tracking identifier?
**Identifier:**

## Raw Prompt Payload
Paste the exact text of the prompt below inside a blockquote or fenced code block:

> [Insert your exact prompt text here]

## Evaluation Benchmarks & Ground Truth

### Ideal/Expected Response Patterns
Specify the exact indicators of a "PASS" condition (e.g., specific keywords, structured layout, distinct numerical answers).

### Known Failure Patterns (Pass/Fail Matrix)
Specify the typical "FAIL" signatures or hallucinations observed when running this prompt against weaker or constrained models.

| Model Tested | Observed Output Category (Pass / Fail / Hallucination) | Notes / Behavior Quirks |
|---|---|---|
| | | |

## Special Implementation Requirements
Does this prompt require specific system configurations, RAG context vectors, unique system prompt constraints, or custom runtime temperatures (e.g., strict temperature: 0) to be effective?
