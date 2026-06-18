### Nuanced Sentiment & Edge Evaluation
**Prompt:**
"Analyze the underlying sentiment of the user review below. Classify it as exactly one of these tokens: [POSITIVE], [NEGATIVE], [NEUTRAL], or [MIXED]. Provide a brief, one-sentence justification explaining your choice.

Review: 'Oh, absolutely wonderful. I ordered the high-end GPU expecting a premium out-of-the-box experience, only to spend four hours troubleshooting driver loops, dealing with a cracked fan casing, and getting hung up on by customer support. Truly a masterpiece of terrible engineering.'"

**Expected Result:**
- Classification: `[NEGATIVE]`.
- This tests if the model gets fooled by the positive anchor words ("absolutely wonderful", "premium", "masterpiece") or correctly parses the heavy sarcasm and technical failure detailed in the core text.