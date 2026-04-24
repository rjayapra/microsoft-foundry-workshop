---
layout: page
title: Agenda
---

## Total Duration

09:00 to 16:00 (full-day workshop)

---

## Session Plan Overview

| Time | Session | Track |
|---|---|---|
| 09:00 – 09:15 | Workshop overview and introductions | All |
| 09:15 – 09:45 | Environment validation | All (Lab 00) |
| 09:45 – 10:30 | Build your first AI agent | Beginner (Lab 01) / Advanced (Adv 01 Part 1) |
| 10:30 – 10:45 | Break | — |
| 10:45 – 11:15 | Extend with MCP tools | Beginner (Lab 02) / Advanced (Adv 02) |
| 11:15 – 12:00 | Build a knowledge base with Foundry IQ | Beginner (Lab 03) / Advanced (Adv 03) |
| 12:00 – 13:00 | Lunch break | — |
| 13:00 – 13:35 | Multi-agent orchestration concepts | Beginner (Lab 04) / Advanced (Adv 08) |
| 13:35 – 15:00 | Advanced track continued | Advanced (Adv 04–07) |
| 15:00 – 15:30 | Participant demos and Q&A | All |
| 15:30 – 16:00 | Debrief, next steps, and close | All |

---

## Session Details

### 1. Workshop Overview and Introductions (09:00 – 09:15)

- Introduce Microsoft Foundry and Azure AI agent architecture.
- Explain the two-track workshop structure: beginner (portal only) and advanced (portal + Python).
- Confirm which track each participant is following.
- Set goals and success criteria.

### 2. Environment Validation — Lab 00 (09:15 – 09:45)

**All participants follow Lab 00.**

- Sign in to Azure portal and confirm subscription access.
- Create or open a Microsoft Foundry project.
- Deploy a GPT-4o or GPT-4.1 model.
- Run a test message in the agent playground.
- Confirm Azure AI Search awareness.

**Beginner participants:** No local tools needed. Browser only.
**Advanced participants:** Also confirm Python, VS Code, and the Foundry extension are installed.

### 3. Build Your First AI Agent (09:45 – 10:30)

**Beginner:** Lab 01 — portal only.
- Create IT Support Agent with instructions.
- Add File search tool with IT_Policy.txt.
- Add Code interpreter with system_performance.csv.
- Test in playground.

**Advanced:** Adv Lab 01 Part 1 (portal) then Part 2 (VS Code + Python).

### 4. Break (10:30 – 10:45)

### 5. Extend with MCP Tools (10:45 – 11:15)

**Beginner:** Lab 02 — connect to the Microsoft Learn Docs MCP server in the portal and test live documentation search.

**Advanced:** Adv Lab 02 — connect to the remote MCP server via Python *and* build a custom local MCP server.

### 6. Build a Knowledge Base with Foundry IQ (11:15 – 12:00)

**Beginner:** Lab 03 — create an Azure AI Search resource, build a Foundry IQ knowledge base from Contoso product docs, create a product agent, and test.

**Advanced:** Adv Lab 03 — same knowledge base, then interact programmatically using the Foundry SDK from VS Code.

### 7. Lunch Break (12:00 – 13:00)

### 8. Multi-Agent Orchestration (13:00 – 13:35)

**Beginner:** Lab 04 — create three specialised agents (Summariser, Classifier, Action Recommender) and simulate the pipeline manually in the playground. Understand *why* specialised agents outperform a single general-purpose agent.

**Advanced:** Adv Lab 08 — automate the same multi-agent pipeline using the Microsoft Agent Framework SDK and Python.

### 9. Advanced Track Continued (13:35 – 15:00)

**Advanced participants only** — continue with remaining advanced labs based on interest and time:
- Adv Lab 04: Deploy agent to Microsoft Teams
- Adv Lab 05: Work IQ (optional)
- Adv Lab 06: Build a workflow in Foundry
- Adv Lab 07: Agent Framework SDK

**Beginner participants:** Use this time to deepen understanding, retry labs, or start the advanced track.

### 10. Participant Demos and Q&A (15:00 – 15:30)

- Each participant (or pair) demonstrates one agent or workflow they built.
- Facilitator highlights interesting approaches and asks discussion questions.
- Address any remaining questions.

### 11. Debrief, Next Steps, and Close (15:30 – 16:00)

- Recap what was covered: agents, MCP tools, knowledge bases, multi-agent patterns.
- Share the [Post-Workshop resources]({{ '/post-workshop.html' | relative_url }}).
- Collect feedback.
- Point participants to the advanced labs if they want to continue learning.
