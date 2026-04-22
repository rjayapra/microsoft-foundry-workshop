---
layout: page
title: "Advanced Lab 05: Work IQ — Workplace Intelligence (Optional)"
nav_order: 14
lab_id: adv-lab-05
category: advanced
---

{% include lab-navigation.html %}

## Lab Summary

Build an AI agent that accesses **Microsoft 365 workplace data** using **Work IQ** — Microsoft's contextual intelligence layer built on the Model Context Protocol (MCP). The agent can prepare for meetings, track projects, extract action items, and answer workplace questions using real M365 data.

> **Important:** This is an **optional lab** that requires a **Microsoft 365 Copilot licence**. It is designed for enterprise learners, Microsoft employees, or those with M365 Copilot access. Standard M365 accounts without Copilot will not work.

## Estimated Time

40 minutes

## Learning Objectives

1. Understand the Work IQ architecture and its MCP-based data access model.
2. Configure an AI agent to use Work IQ tools via MCP.
3. Build a workplace intelligence agent in Python using the Foundry SDK.
4. Demonstrate five workplace intelligence scenarios in a single interactive session.

## Prerequisites

- An Azure subscription with Contributor access.
- A **Microsoft 365 Copilot** licence.
- Visual Studio Code installed.
- Python 3.12 or later installed.

---

## Step 1: Understand Work IQ and MCP

Work IQ exposes Microsoft 365 data (calendar, email, Teams, tasks, documents) as MCP-compatible tool endpoints. When an agent is configured with Work IQ, it can:

- **Meeting prep** — summarise upcoming meetings and relevant documents.
- **Project tracking** — surface tasks, owners, and deadlines from Planner / To Do.
- **Action item extraction** — identify follow-up actions from emails and meeting notes.
- **Workplace Q&A** — answer questions using real-time M365 context.
- **Document summarisation** — condense SharePoint documents on demand.

## Step 2: Set up the environment

1. Clone the workshop repository (if you haven't already):
   ```bash
   git clone https://github.com/rjayapra/microsoft-foundry-workshop.git
   cd microsoft-foundry-workshop
   ```
   Then navigate to `Labfiles/adv-lab-05-work-iq/Python`.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Create a `.env` file with your Foundry project and M365 credentials:
   ```
   PROJECT_CONNECTION_STRING=<your-connection-string>
   TENANT_ID=<your-m365-tenant-id>
   CLIENT_ID=<app-registration-client-id>
   CLIENT_SECRET=<app-registration-client-secret>
   ```

## Step 3: Explore Work IQ tool configuration

1. Open `workiq_lab.py` — the unified interactive application.
2. Locate the `WORK_IQ_MCP_ENDPOINT` variable and verify it points to:
   ```
   https://workiq.microsoft.com/api/mcp
   ```
3. Review how the agent is configured with Work IQ as an MCP tool server.

## Step 4: Run the five-scenario demonstration

1. Start the interactive application:
   ```bash
   python workiq_lab.py
   ```
2. Follow the on-screen menu to run each scenario:

   | # | Scenario | Example prompt |
   |---|----------|----------------|
   | 1 | Meeting prep | *"Prepare me for my 2 PM meeting on Azure migration."* |
   | 2 | Project tracking | *"List open tasks assigned to me this week."* |
   | 3 | Action item extraction | *"What action items came out of yesterday's review meeting?"* |
   | 4 | Workplace Q&A | *"Who is the owner of the DevOps pipeline modernisation project?"* |
   | 5 | Document summarisation | *"Summarise the Q2 roadmap document in Teams."* |

3. Observe how the agent calls Work IQ MCP tools to retrieve real-time M365 data.

---

## Clean up

No Azure resources are specifically created in this lab beyond the Foundry project.  
Delete the Azure resource group when you are done with all Advanced Labs.

## Summary

In this optional lab you:
- Configured an agent with Work IQ MCP tools to access M365 workplace data.
- Ran five workplace intelligence scenarios against live Microsoft 365 data.
- Demonstrated how MCP enables agents to work across enterprise data boundaries.

**Next:** [Advanced Lab 06: Build a Workflow in Microsoft Foundry]({{ '/adv-lab-06-foundry-workflow.html' | relative_url }})
