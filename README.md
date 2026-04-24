# Microsoft Foundry Workshop

A hands-on workshop for building AI agents with **Microsoft Foundry**. The workshop has two tracks: a **beginner track** that works entirely in the browser (no coding required), and an **advanced track** that introduces programmatic agent development with Python and the Foundry SDK.

---

## Workshop Tracks

### 🟢 Beginner Track — Browser only, no coding required

Perfect for participants who are new to Microsoft Foundry and Azure AI. All steps use the Foundry portal at [https://ai.azure.com](https://ai.azure.com).

**Total time:** ~3 hours  
**Requirements:** Azure subscription + web browser

| Lab | Topic | Time |
|---|---|---|
| [Lab 00](docs/lab-00-environment-validation.md) | Environment Validation | 30 min |
| [Lab 01](docs/lab-01-first-autonomous-agent.md) | Build Your First AI Agent | 45 min |
| [Lab 02](docs/lab-02-mcp-tools-portal.md) | Extend Your Agent with MCP Tools | 30 min |
| [Lab 03](docs/lab-03-foundry-iq-portal.md) | Build a Knowledge Base with Foundry IQ | 45 min |
| [Lab 04](docs/lab-04-multi-agent-portal.md) | Multi-Agent Orchestration Concepts | 35 min |

### 🔵 Advanced Track — Python + VS Code required

Build on beginner track concepts with programmatic agent development using the Foundry SDK.

**Total time:** ~5 hours  
**Requirements:** Python 3.12+, VS Code, Microsoft Foundry VS Code extension

| Lab | Topic | Time |
|---|---|---|
| [Adv Lab 01](docs/adv-lab-01-build-agent-portal-vscode.md) | Build AI Agents with Portal and VS Code | 45 min |
| [Adv Lab 02](docs/adv-lab-02-mcp-integration.md) | Extend Agents with MCP Tools (Python) | 60 min |
| [Adv Lab 03](docs/adv-lab-03-foundry-iq.md) | Integrate Agent with Foundry IQ (Python) | 45 min |
| [Adv Lab 04](docs/adv-lab-04-m365-teams.md) | Deploy Agents to Microsoft Teams | 40 min |
| [Adv Lab 05](docs/adv-lab-05-work-iq.md) | Work IQ — Workplace Intelligence (Optional) | 40 min |
| [Adv Lab 06](docs/adv-lab-06-foundry-workflow.md) | Build a Workflow in Foundry | 45 min |
| [Adv Lab 07](docs/adv-lab-07-agent-framework.md) | Microsoft Agent Framework SDK | 30 min |
| [Adv Lab 08](docs/adv-lab-08-multi-agent-framework.md) | Multi-Agent Solution with Agent Framework | 30 min |

---

## Workshop Outcomes

By the end of this workshop, participants will be able to:

**Beginner track:**
1. Create and configure AI agents in the Microsoft Foundry portal.
2. Write clear, effective agent instructions.
3. Ground agents in documents using File search and Foundry IQ knowledge bases.
4. Connect agents to live external tools using MCP.
5. Understand and simulate multi-agent orchestration patterns.

**Advanced track (in addition to the above):**
6. Build and run agents programmatically using the Foundry Python SDK.
7. Create custom MCP servers and expose them to agents.
8. Interact with Foundry IQ knowledge bases from code.
9. Deploy agents to Microsoft Teams and Microsoft 365 Copilot.
10. Implement automated multi-agent pipelines with the Agent Framework SDK.

---

## Planning Documents

- [Agenda](docs/agenda.md)
- [Facilitator Guide](docs/facilitator-guide.md)
- [Prerequisites](docs/prerequisites.md)
- [Troubleshooting Guide](docs/troubleshooting.md)
- [Post-Workshop Follow-Up](docs/post-workshop.md)

---

## Recommended Delivery Format

| Format | Details |
|---|---|
| Duration | Half-day (beginner track only) or full-day (both tracks) |
| Audience | Anyone new to Microsoft Foundry / AI agents |
| Skill level — Beginner | Azure portal access, no coding |
| Skill level — Advanced | Python experience + Azure AI familiarity |

---

## Lab Files

Sample data files used in the labs are in the `Labfiles/` folder:

- `Labfiles/adv-lab-01-build-agent-portal-vscode/` — IT_Policy.txt and system_performance.csv (used in Beginner Lab 01 and Adv Lab 01)
- `Labfiles/adv-lab-03-foundry-iq/data/` — Contoso product markdown files (used in Beginner Lab 03 and Adv Lab 03)

## Source Attribution

This workshop structure is inspired by Microsoft Logic Apps Labs content:

- Category page: https://azure.github.io/logicapps-labs/docs/category/build-autonomous-agentic-workflows
- Advanced lab content adapted from: https://github.com/MicrosoftLearning/mslearn-ai-agents
