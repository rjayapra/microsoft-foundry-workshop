---
layout: home
title: Microsoft Foundry Workshop
description: Hands-on workshop to build, debug, and operationalize autonomous agentic workflows with Microsoft Foundry and Azure Logic Apps.
---

Build, validate, and scale autonomous agentic workflows with Microsoft Foundry and Azure Logic Apps.

<p class="cta-group">
  <a class="cta-button" href="{{ '/prerequisites.html' | relative_url }}" aria-label="Open workshop prerequisites">Prerequisites</a>
  <a class="cta-button" href="{{ '/agenda.html' | relative_url }}" aria-label="Open workshop agenda">Agenda</a>
  <a class="cta-button" href="{{ '/lab-00-environment-validation.html' | relative_url }}" aria-label="Start Lab 00 environment validation">Start Lab 00</a>
  <a class="cta-button" href="{{ '/adv-lab-01-build-agent-portal-vscode.html' | relative_url }}" aria-label="Start Advanced Labs">Start Advanced Labs</a>
</p>

## Workshop Flow

1. **Pre-workshop**: Confirm environment, access, and readiness.
2. **Beginner labs**: Build an agent, connect tools, debug behaviour, and evaluate quality.
3. **Advanced labs**: Deepen skills with programmatic agent development, MCP, multi-agent orchestration, Teams deployment, and Foundry workflows.
4. **Wrap-up**: Review outcomes, demos, and post-workshop next steps.

### Guided path

- **Pre-workshop** → [Prerequisites]({{ '/prerequisites.html' | relative_url }})
- **Beginner** → [Lab 00]({{ '/lab-00-environment-validation.html' | relative_url }}) · [Lab 01]({{ '/lab-01-first-autonomous-agent.html' | relative_url }}) · [Lab 02]({{ '/lab-02-debug-autonomous-agent.html' | relative_url }}) · [Lab 03]({{ '/lab-03-connect-tools-external-services.html' | relative_url }}) · [Lab 04]({{ '/lab-04-foundry-evaluation-and-automation.html' | relative_url }}) · [Lab 05]({{ '/lab-05-end-to-end-scaleout-and-demos.html' | relative_url }})
- **Advanced** → [Adv 01]({{ '/adv-lab-01-build-agent-portal-vscode.html' | relative_url }}) · [Adv 02]({{ '/adv-lab-02-mcp-integration.html' | relative_url }}) · [Adv 03]({{ '/adv-lab-03-foundry-iq.html' | relative_url }}) · [Adv 04]({{ '/adv-lab-04-m365-teams.html' | relative_url }}) · [Adv 05]({{ '/adv-lab-05-work-iq.html' | relative_url }}) · [Adv 06]({{ '/adv-lab-06-foundry-workflow.html' | relative_url }}) · [Adv 07]({{ '/adv-lab-07-agent-framework.html' | relative_url }}) · [Adv 08]({{ '/adv-lab-08-multi-agent-framework.html' | relative_url }})
- **Wrap-up** → [Troubleshooting]({{ '/troubleshooting.html' | relative_url }}) · [Post-workshop]({{ '/post-workshop.html' | relative_url }})

## Workshop Documents

### Plan & preparation

- [Agenda]({{ '/agenda.html' | relative_url }})
- [Facilitator guide]({{ '/facilitator-guide.html' | relative_url }})
- [Prerequisites]({{ '/prerequisites.html' | relative_url }})

### 🟢 Beginner Labs {#beginner-labs}

These labs introduce Microsoft Foundry fundamentals: creating agents, connecting tools, debugging, and evaluating quality. Designed for participants new to Foundry and Azure AI services.

{% assign beginner_labs = site.data.labs | where: "category", "beginner" %}
{% for lab in beginner_labs %}
- [{{ lab.title }}]({{ lab.url | relative_url }}){% if lab.duration %} — {{ lab.duration }} min{% endif %}
{% endfor %}

### 🔵 Advanced Labs {#advanced-labs}

These labs build on Beginner skills and require Python 3.12+ and Visual Studio Code. Topics include programmatic agent development with the Foundry SDK, MCP tool integration, Foundry IQ knowledge bases, Teams deployment, and multi-agent orchestration with the Agent Framework SDK.

{% assign advanced_labs = site.data.labs | where: "category", "advanced" %}
{% for lab in advanced_labs %}
- [{{ lab.title }}]({{ lab.url | relative_url }}){% if lab.duration %} — {{ lab.duration }} min{% endif %}
{% endfor %}

### Support & closeout

- [Troubleshooting]({{ '/troubleshooting.html' | relative_url }})
- [Post-workshop follow-up]({{ '/post-workshop.html' | relative_url }})
