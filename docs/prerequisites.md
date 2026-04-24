---
layout: page
title: Prerequisites
---

Use this checklist at least 3 days before delivery.

---

## Beginner Track Prerequisites

The beginner track runs **entirely in a web browser**. No local tools are required.

### What every beginner participant needs

1. **Active Azure subscription** with at least **Contributor** access to a resource group.
2. **Browser** — Microsoft Edge or Google Chrome recommended.
3. Access to [https://portal.azure.com](https://portal.azure.com) (not blocked by corporate proxy or firewall).
4. Access to [https://ai.azure.com](https://ai.azure.com) (Microsoft Foundry portal — not blocked).
5. Sufficient **quota** in the selected Azure region to deploy a GPT-4o or GPT-4.1 model. Confirm before the workshop day.

### What the facilitator should pre-provision for beginners

- If participants **cannot create Azure subscriptions themselves**, pre-create a Foundry project for each participant and share connection details.
- Confirm the target Azure region has available quota for **Standard** or **Global Standard** model deployments.
- Have a backup region ready (for example, if East US 2 is full, use Sweden Central).
- Download and stage the lab files so participants can easily access them:
  - `IT_Policy.txt`
  - `system_performance.csv`
  - `contoso-products.zip` (product markdown files)

---

## Advanced Track Prerequisites

The advanced track requires local development tools in addition to the beginner prerequisites.

### What every advanced participant needs

1. Everything in the beginner prerequisites (above).
2. **Python 3.12 or later** installed ([https://www.python.org/downloads](https://www.python.org/downloads)).
3. **Visual Studio Code** installed ([https://code.visualstudio.com](https://code.visualstudio.com)).
4. **Microsoft Foundry VS Code extension** (v0.16.0 or later) — install from the VS Code Extensions marketplace.
5. **Git** installed ([https://git-scm.com](https://git-scm.com)).
6. Access to clone: `https://github.com/rjayapra/microsoft-foundry-workshop`

### Pre-workshop validation for advanced track

Run the following in a terminal to confirm local tooling:

```bash
python --version    # must be 3.12 or later
code --version
git --version
```

---

## Azure Resource Checklist

Facilitators: confirm these resources exist **before workshop day**.

| Resource | Beginner track | Advanced track |
|---|---|---|
| Azure subscription (Contributor access) | Required | Required |
| Resource group | Required | Required |
| Microsoft Foundry project | Required | Required |
| GPT-4o or GPT-4.1 model deployment | Required | Required |
| Azure AI Search service | Required (Lab 03) | Required (Adv Lab 03) |
| Python 3.12+ | Not required | Required |
| VS Code + Foundry extension | Not required | Required |

---

## Cost and Quota Notes

- Agent runs consume model tokens. Estimate ~500–2000 tokens per test interaction.
- Azure AI Search Basic tier is sufficient for the workshop and costs under $1/day.
- All beginner labs can be completed with a single gpt-4o Standard deployment.
- Validate regional model availability using the [Azure AI model quota page](https://ai.azure.com) before workshop day.

---

## Facilitator Preparation Checklist

1. Validate all labs end to end in a clean subscription.
2. Prepare a backup demo environment (second Foundry project in a different region).
3. Download and test all lab files work for upload in the Foundry portal.
4. Confirm no tenant policies block file uploads or MCP server connections.
5. Have model deployment names and connection strings ready for participants who fall behind.
6. Stage the lab files at an easily shareable URL if participants cannot clone the repo.
