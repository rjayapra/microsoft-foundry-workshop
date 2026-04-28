---
layout: page
title: Facilitator Guide
---

## How to Use This Guide

This guide helps you run the two-track workshop smoothly with clear pacing, checkpoints, and fallback options for both beginner (portal only) and advanced (portal + Python) participants.

---

## Workshop Tracks at a Glance

| | Beginner Track | Advanced Track |
|---|---|---|
| **Tools** | Browser only (ai.azure.com) | Python 3.12+, VS Code, Foundry extension |
| **Labs** | Lab 00 – Lab 04 | Adv Lab 01 – Adv Lab 08 |
| **Time** | ~3 hours hands-on | ~5 hours hands-on |
| **Audience** | New to Foundry | Familiar with Foundry or dev background |

---

## Delivery Strategy

1. **Demo first, then let participants execute.** Show the completed outcome for each lab before participants start — this sets expectations and reduces confusion.
2. **Keep a checkpoint every 20 minutes.** Call the group back after each lab to compare results and address common issues before they compound.
3. **Encourage pairs.** One person configures while the other validates and navigates. Both participants should swap roles across labs.
4. **Separate the tracks early.** At the end of Lab 00, confirm which participants are on the beginner track and which on the advanced track. Point beginner-track participants to Lab 01 and advanced-track participants to Adv Lab 01.
5. **Never leave a participant stuck alone for more than 5 minutes.** Pair them with a neighbour or have them skip to the next lab.

---

## Required Facilitator Assets

1. One **ready-to-run Foundry project** with a healthy GPT-5.1 deployment to use for live demos.
2. One **backup model deployment** in a second region in case quota runs out.
3. Lab files pre-downloaded and staged:
   - `IT_Policy.txt` and `system_performance.csv` for Lab 01 / Adv Lab 01
   - `contoso-products.zip` (extracted) for Lab 03 / Adv Lab 03
4. Screen captures of each lab's expected final state for participants who fall behind.
5. The workshop repository cloned and tested on your machine for the advanced demo:
   ```bash
   git clone https://github.com/rjayapra/microsoft-foundry-workshop.git
   ```

---

## Live Demo Sequence (per-lab)

For each lab, use this pattern:
1. **Show the finished state first** (30 seconds) — open your completed agent, run a quick test, show the response.
2. **Show the architecture** (1–2 minutes) — explain what components are involved and how they connect.
3. **Walk through build steps** with participants executing alongside you.
4. **Call checkpoint** — verify everyone reached the expected state before moving on.

---

## Common Failure Modes and Fast Recovery

### Lab 00 — Environment Validation

| Problem | Recovery |
|---|---|
| Participant cannot access ai.azure.com | Check tenant/corporate network; try a personal hotspot to isolate network policy issues |
| Model deployment fails with quota error | Switch to a different region (Sweden Central, West Europe, Australia East) |
| "No subscriptions found" in portal | Account is not linked to the right tenant; check the tenant selector in the top-right corner of the portal |

### Lab 01 — Build First Agent

| Problem | Recovery |
|---|---|
| File search does not find content in IT_Policy.txt | Verify file shows "Indexed" status in the vector store; re-upload if needed |
| Code interpreter does not run on the CSV | Confirm the file is attached to Code interpreter (not File search) |
| Agent gives generic answers | Check that instructions explicitly name the tools and when to use them |

### Lab 02 — MCP Tools

| Problem | Recovery |
|---|---|
| MCP server URL gives an error | Confirm the URL is exactly `https://learn.microsoft.com/api/mcp` — no trailing slash |
| No tools appear after connecting | Server may be temporarily unavailable; wait 1 minute and retry |
| Agent doesn't call the MCP tool | Update instructions: add "Always use the search documentation tool for questions about Microsoft products" |

### Lab 03 — Foundry IQ Knowledge Base

| Problem | Recovery |
|---|---|
| Azure AI Search creation fails | Check subscription quota; try a Basic tier in a different region |
| Documents show "Failed" indexing status | Try re-uploading the individual file; confirm the file is valid Markdown |
| Agent invents product names | Knowledge base is not properly connected — verify Foundry IQ appears and is selected in the Tools section |

### Lab 04 — Multi-Agent Concepts

| Problem | Recovery |
|---|---|
| Classifier returns more than one word | Adjust instructions: add "Respond with ONLY the category label, no punctuation, no explanation" |
| Summariser writes multiple sentences | Adjust instructions: add "Your response must be EXACTLY one sentence. If you write more than one sentence, that is an error." |

---

## Checkpoints

### After Lab 00

- Participant has an active Foundry project.
- Model deployment is confirmed healthy.
- Participant ran a test message in the agent playground and received a response.
- Advanced-track participants also confirmed Python, VS Code, and Foundry extension.

### After Lab 01

- Agent `it-support-agent` exists in the Foundry project.
- File search is connected with `IT_Policy.txt` indexed.
- Code interpreter is enabled with `system_performance.csv` uploaded.
- Agent responds correctly to both the policy question and the data analysis question.

### After Lab 02

- MCP connection to `https://learn.microsoft.com/api/mcp` is active.
- Agent returns documentation-sourced answers when asked about Microsoft services.

### After Lab 03

- Azure AI Search resource is connected to the project.
- `contoso-products-kb` knowledge base has all three documents indexed.
- Agent `contoso-product-agent` returns product-specific answers citing documents.

### After Lab 04

- Three agents created: `summariser-agent`, `classifier-agent`, `action-recommender-agent`.
- Participant successfully ran both sample feedback items through all three stages.
- Participant can explain why specialised agents produce better outputs than a single general agent.

---

## Suggested Challenge Prompts (for fast finishers)

**Beginner track:**
1. Add a second topic to the IT policy agent instructions and test how it handles mixed questions.
2. Add a fourth product category to the Contoso knowledge base and test retrieval.
3. Add a fourth agent to the multi-agent pipeline that scores sentiment on a scale of 1–10.

**Advanced track:**
1. Create a custom MCP server that returns weather data and connect it to an agent.
2. Modify the Agent Framework pipeline to handle all three feedback samples and write results to a CSV file.
3. Connect the Foundry IQ knowledge base to an agent programmatically and compare latency with the portal.

---

## Debrief Questions

1. When would you use File search vs Foundry IQ knowledge base for agent grounding?
2. What makes a good MCP tool description, and how does it affect agent tool selection?
3. Why do specialised agents in a pipeline outperform a single agent asked to do everything?
4. What are the main differences between building agents in the portal vs programmatically with the SDK?
5. How would you test and evaluate agent quality in a production scenario?
