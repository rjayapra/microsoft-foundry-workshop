---
layout: home
title: Microsoft Foundry Workshop
description: Hands-on workshop to build, configure, and extend AI agents with Microsoft Foundry — no coding required for the beginner track.
---

Build and extend AI agents with Microsoft Foundry. The **beginner track** works entirely in the browser using the Foundry portal — no Python, no VS Code, no command line needed. The **advanced track** introduces programmatic agent development with the Foundry SDK and Python.

<p class="cta-group">
  <a class="cta-button" href="{{ '/prerequisites.html' | relative_url }}" aria-label="Open workshop prerequisites">Prerequisites</a>
  <a class="cta-button" href="{{ '/agenda.html' | relative_url }}" aria-label="Open workshop agenda">Agenda</a>
  <a class="cta-button" href="{{ '/lab-00-environment-validation.html' | relative_url }}" aria-label="Start Lab 00 environment validation">Start Beginner Track</a>
  <a class="cta-button" href="{{ '/adv-lab-01-build-agent-portal-vscode.html' | relative_url }}" aria-label="Start Advanced Labs">Start Advanced Track</a>
</p>

## Workshop Tracks

### 🟢 Beginner Track — Browser only, no coding

Perfect for participants who are new to Microsoft Foundry and Azure AI. All steps use the Foundry portal at [https://ai.azure.com](https://ai.azure.com).

**Total time:** ~3 hours

| Lab | Topic | Time |
|---|---|---|
| [Lab 00]({{ '/lab-00-environment-validation.html' | relative_url }}) | Environment Validation | 30 min |
| [Lab 01]({{ '/lab-01-first-autonomous-agent.html' | relative_url }}) | Build Your First AI Agent | 45 min |
| [Lab 02]({{ '/lab-02-mcp-tools-portal.html' | relative_url }}) | Extend Your Agent with MCP Tools | 30 min |
| [Lab 03]({{ '/lab-03-foundry-iq-portal.html' | relative_url }}) | Build a Knowledge Base with Foundry IQ | 45 min |
| [Lab 04]({{ '/lab-04-multi-agent-portal.html' | relative_url }}) | Multi-Agent Orchestration Concepts | 35 min |

### 🔵 Advanced Track — Python + VS Code required

These labs build on beginner track concepts and require **Python 3.12+** and **Visual Studio Code**. Topics include programmatic agent development with the Foundry SDK, MCP tool integration, Foundry IQ knowledge bases, Teams deployment, and multi-agent orchestration with the Agent Framework SDK.

**Prerequisites for advanced track:** Complete the beginner track first (or be familiar with Foundry portal basics).

| Lab | Topic | Time |
|---|---|---|
| [Adv 01]({{ '/adv-lab-01-build-agent-portal-vscode.html' | relative_url }}) | Build AI Agents with Portal and VS Code | 45 min |
| [Adv 02]({{ '/adv-lab-02-mcp-integration.html' | relative_url }}) | Extend Agents with MCP Tools (Python) | 60 min |
| [Adv 03]({{ '/adv-lab-03-foundry-iq.html' | relative_url }}) | Integrate Agent with Foundry IQ (Python) | 45 min |
| [Adv 04]({{ '/adv-lab-04-m365-teams.html' | relative_url }}) | Deploy Agents to Microsoft Teams | 40 min |
| [Adv 05]({{ '/adv-lab-05-work-iq.html' | relative_url }}) | Work IQ — Workplace Intelligence (Optional) | 40 min |
| [Adv 06]({{ '/adv-lab-06-foundry-workflow.html' | relative_url }}) | Build a Workflow in Microsoft Foundry | 45 min |
| [Adv 07]({{ '/adv-lab-07-agent-framework.html' | relative_url }}) | Microsoft Agent Framework SDK | 30 min |
| [Adv 08]({{ '/adv-lab-08-multi-agent-framework.html' | relative_url }}) | Multi-Agent Solution with Agent Framework | 30 min |

---

## Workshop Documents

### Plan & preparation

- [Agenda]({{ '/agenda.html' | relative_url }})
- [Facilitator guide]({{ '/facilitator-guide.html' | relative_url }})
- [Prerequisites]({{ '/prerequisites.html' | relative_url }})

### 🟢 Beginner Labs — Portal only {#beginner-labs}

These labs introduce Microsoft Foundry fundamentals: creating agents, grounding with documents, connecting MCP tools, building knowledge bases, and understanding multi-agent patterns. Designed for participants new to Foundry and Azure AI services. **No coding or local tools required.**

{% assign beginner_labs = site.data.labs | where: "category", "beginner" %}
{% for lab in beginner_labs %}
- [{{ lab.title }}]({{ lab.url | relative_url }}){% if lab.duration %} — {{ lab.duration }} min{% endif %}
{% endfor %}

### 🔵 Advanced Labs — Python + VS Code {#advanced-labs}

These labs build on beginner track skills and require Python 3.12+ and Visual Studio Code. Topics include programmatic agent development with the Foundry SDK, MCP tool integration, Foundry IQ knowledge bases, Teams deployment, and multi-agent orchestration with the Agent Framework SDK.

{% assign advanced_labs = site.data.labs | where: "category", "advanced" %}
{% for lab in advanced_labs %}
- [{{ lab.title }}]({{ lab.url | relative_url }}){% if lab.duration %} — {{ lab.duration }} min{% endif %}
{% endfor %}

### Support & closeout

- [Troubleshooting]({{ '/troubleshooting.html' | relative_url }})
- [Post-workshop follow-up]({{ '/post-workshop.html' | relative_url }})
