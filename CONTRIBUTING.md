# Contributing to Edge AI Debugging

We welcome contributions to help improve our diagnostic prompt library! Whether you have a new edge case test or a fix for an existing one, please follow these guidelines.

## How to Contribute
1. **Fork the repository.**
2. **Create a feature branch:** `git checkout -b feature/new-diagnostic-test`
3. **Add your test:** Create a new markdown file in the root directory following the `llm-debugger-X.md` naming convention.
4. **Follow the format:** Ensure your file includes:
   - **Title**
   - **Prompt**
   - **Expected Result**
5. **Submit a Pull Request.**

## Best Practices
- **Isolation:** Ensure your prompt does not rely on hidden context.
- **Determinism:** If possible, write prompts that yield clear pass/fail results.
- **Security:** Adhere to the `SECURITY.md` guidelines—never include PII or sensitive production secrets in your test data.
- **Style:** Keep any explanatory copy concise, technical, and direct. Use short sentences and pattern-focused language when describing model behavior.

## Code of Conduct
By participating, you agree to follow the repository's [Code of Conduct](CODE_OF_CONDUCT.md) and to uphold professional, respectful interaction in all project spaces.
