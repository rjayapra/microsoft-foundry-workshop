---
layout: page
title: Post-Workshop
---

## Recommended Next Steps for Customer Team

1. Move from static tool inputs to parameterized inputs.
2. Add user confirmation for any write operations.
3. Add robust retry and fallback logic for external services.
4. Add standardized telemetry and run analytics.
5. Establish prompt and tool review process for production.

## Production Hardening Checklist

1. Security
- Use managed identity when available.
- Store secrets in Azure Key Vault.
- Apply least privilege access to connectors.

2. Reliability
- Add retries and timeout handling.
- Implement graceful user messaging for transient failures.
- Include dead-letter or alerting path for repeated failures.

3. Observability
- Monitor run failures and latency.
- Track model token usage and cost trends.
- Capture tool success and failure rates.

4. Governance
- Version prompts and workflow definitions.
- Define approval flow for prompt updates.
- Document incident response runbooks.

## Optional Advanced Exercises

1. Add dynamic parameters to tool inputs.
2. Add a second model and compare behavior.
3. Build a role-based tool access pattern.
4. Add MCP tools for internal enterprise systems.

## References

- Logic Apps Labs category:
  - https://azure.github.io/logicapps-labs/docs/category/build-autonomous-agentic-workflows
- Azure AI Foundry:
  - https://learn.microsoft.com/azure/ai-foundry/
- Evaluate generative AI apps:
  - https://learn.microsoft.com/azure/ai-foundry/how-to/evaluate-sdk
- Azure Logic Apps autonomous agents docs:
  - https://learn.microsoft.com/azure/logic-apps/create-agent-workflows
- Azure connector overview:
  - https://learn.microsoft.com/azure/connectors/introduction
