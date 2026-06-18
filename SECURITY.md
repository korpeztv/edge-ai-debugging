# Security Policy

## Overview

This repository contains diagnostic prompts and testing methodologies for evaluating Large Language Model (LLM) behavior, particularly in edge computing environments. Given the nature of LLM testing and prompt engineering, security is paramount to prevent prompt injection, jailbreaks, and model exploitation.

## Supported Versions

| Version | Supported          |
| ------- | -------- |
| 1.x+    | ✅ Active Support   |
| < 1.0   | ❌ No Support      |

## Reporting a Vulnerability

**Do not open public issues for security vulnerabilities.** Instead:

1. **Email**: Send a detailed report to the repository maintainers with:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested remediation

2. **Timeline**: We aim to respond within **48 hours** and provide updates every **7 days**.

3. **Disclosure**: We follow **responsible disclosure** practices and will coordinate a fix before public announcement.

## Security Considerations

### 1. Prompt Injection & Jailbreak Prevention

This repository's diagnostic tests intentionally probe for prompt injection vulnerabilities. When using these tests:

- **Isolate System and User Prompts**: Always keep system prompts and user input separate in your implementation.
- **Input Validation**: Sanitize and validate all user-supplied prompts before passing to LLM APIs.
- **Rate Limiting**: Implement request throttling to prevent abuse of edge-deployed models.
- **Audit Logging**: Log all LLM interactions for security review.

### 2. Model Output Validation

Test outputs should be validated server-side.

### 3. Context Window Security

When testing with large context payloads (like the "Lost in the Middle" test):

- **Sanitize Logs**: Remove sensitive data (API keys, tokens, PII) from test logs before submission.
- **Context Size Limits**: Set reasonable limits on context injection to prevent memory exhaustion.
- **Verify Extraction**: Ensure models extract *only* requested data, not extraneous information.

### 4. Temporal & Knowledge Cutoff Handling

The temporal anchor test exposes model knowledge cutoff issues. In production:

- **Anchor Date Context**: Always provide the current date explicitly in system prompts.
- **Train/Test Split**: Use a fixed date for consistency across test runs.
- **Monitor Drift**: Track if model behavior changes with real-time date updates.

### 5. API Key & Credential Management

When running diagnostic tests against production models:

- **Use Environment Variables**: Store API keys in `.env` or secure vaults, **never in code**.
- **Separate Test Credentials**: Use dedicated test API credentials with restricted permissions.
- **Rotate Keys Regularly**: Implement key rotation policies for production models.
- **Monitor API Usage**: Track usage patterns for anomalies indicating compromise.

### 6. Data Privacy in Tests

Diagnostic prompts should not contain:

- Real user data or PII
- Production secrets or internal credentials
- Proprietary business logic or algorithms
- Real financial or health information

Use **synthetic test data** for all scenarios.

### 7. Model Hallucination & Grounding

The hallucination audit test (Test #4) verifies grounding capability. In production:

- **Verify Sources**: Always check if model-provided facts are backed by provided context.
- **Fail Safely**: Return "Information not found" rather than guessed or hallucinated data.
- **Trust Boundaries**: Don't cascade model outputs without validation.

### 8. Tool & Function Call Security

The agentic tool hallucination test (Test #8) prevents parameter injection:

- **Validate Tool Calls**: Reject function calls with undeclared or extra parameters.
- **Schema Enforcement**: Strictly enforce function signatures before execution.
- **Parameterize Queries**: Never allow direct SQL/command injection from model outputs.

### 9. Edge Deployment Security

For edge-deployed models (Cloudflare Workers, etc.):

- **Resource Limits**: Cap inference time and memory to prevent DoS attacks.
- **Cold Start Security**: Ensure models are loaded securely on first invocation.
- **Output Sanitization**: Strip debugging info, internal errors from edge responses.
- **CORS & Headers**: Validate origin and set appropriate security headers.

### 10. Monitoring & Alerting

Implement continuous monitoring for:

- **Prompt Injection Attempts**: Flag suspicious pattern inputs.
- **Unexplained Refusals**: Alert on models refusing to answer valid questions.
- **Performance Degradation**: Monitor inference latency for anomalies.
- **Output Anomalies**: Track when model outputs deviate from expected distributions.

## Best Practices

### ✅ DO

- Test models in isolated sandbox environments first.
- Version-control diagnostic prompts for reproducibility.
- Document expected vs. actual model behavior.
- Use deterministic settings (`temperature=0`) during testing.
- Implement comprehensive error handling around model calls.
- Regularly audit and update diagnostic tests.
- Use typed validation for all model outputs.

### ❌ DON'T

- Deploy untested prompts to production.
- Mix sensitive production data with diagnostic prompts.
- Ignore model refusals or error messages.
- Rely solely on model output without server-side validation.
- Store API keys or credentials in repositories.
- Test prompt injection attacks on live production systems.
- Skip security testing for edge-deployed models.

## Security Testing Checklist

Before deploying any LLM-based system:

- [ ] Run all 10 diagnostic tests against target model.
- [ ] Document expected vs. actual results.
- [ ] Implement input validation for all user prompts.
- [ ] Set up rate limiting and DDoS protection.
- [ ] Enable comprehensive audit logging.
- [ ] Validate all model outputs server-side.
- [ ] Test with synthetic, non-sensitive data only.
- [ ] Review model refusal behavior.
- [ ] Implement monitoring and alerting.
- [ ] Conduct security review with team.
- [ ] Document known limitations and workarounds.

## Third-Party Dependencies

This repository has minimal dependencies. However, when using:

- **Cloudflare Workers AI**: Review their security documentation at https://developers.cloudflare.com/workers-ai/security/
- **LLM APIs**: Follow provider's security best practices.
- **Node/Runtime**: Keep runtime versions updated and patched.

## License & Compliance

- **License**: Check LICENSE file for terms.
- **Compliance**: Ensure LLM usage complies with local regulations (GDPR, CCPA, etc.).
- **Terms of Service**: Abide by API provider's ToS regarding testing and prompt injection.

## Contact & Support

For security questions:

- **Issues**: Use private security advisories on GitHub.
- **Email**: Contact maintainers directly.
- **Discussion**: Open a private discussion for non-critical security topics.

## Changelog

See CHANGELOG.md for security-related updates and patch notes.

---

Last Updated: June 18, 2026
Version: 1.0
Maintained By: korpeztv
