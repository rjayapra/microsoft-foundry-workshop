---
layout: page
title: "Advanced Lab 06: Build a Workflow in Microsoft Foundry"
nav_order: 15
lab_id: adv-lab-06
category: advanced
---

{% include lab-navigation.html %}

## Lab Summary

Use the **Microsoft Foundry portal** to build a **sequential workflow** that automates customer support ticket resolution. Workflows are visual, UI-based tools for defining action sequences involving AI agents, conditional logic, and loops — no code required to set up the pipeline.

## Estimated Time

45 minutes

## Learning Objectives

1. Create a sequential workflow in the Microsoft Foundry portal.
2. Configure a for-each loop to process multiple support tickets.
3. Integrate an AI agent (Triage Agent) as a workflow node.
4. Implement conditional logic to handle low-confidence classifications.
5. Invoke the workflow programmatically using the Foundry SDK.

## Prerequisites

- An Azure subscription with Contributor access.
- Visual Studio Code installed.
- Python 3.12 or later installed.

---

## Workflow Overview

The workflow you'll build processes **ContosoPay customer support tickets** through this pipeline:

1. **Input** — a predefined array of customer support issue descriptions.
2. **For-each loop** — iterates over each ticket independently.
3. **Triage Agent** — classifies each ticket as *Billing*, *Technical*, or *General* with a confidence score.
4. **Conditional logic** — if confidence < 0.7, flags the ticket for additional information.
5. **Response Agent** — generates a recommended response for *Technical* and *General* tickets.
6. **Output** — structured JSON per ticket with classification, confidence, and recommended response.

---

## Part 1 — Build the workflow in the portal

### Step 1: Create a Foundry project

1. Open [https://ai.azure.com](https://ai.azure.com) and sign in.
2. Create or open a Foundry project.
3. Navigate to **Workflows** in the left sidebar.

### Step 2: Create a blank sequential workflow

1. Select **+ New workflow → Blank workflow**.
2. Name the workflow `support-ticket-workflow`.
3. The canvas opens with an **Input** node and an **Output** node.

### Step 3: Add a for-each loop

1. Select **+ Add node** between Input and Output.
2. Choose **For each** from the node menu.
3. Set the loop input to `@{triggerBody().tickets}` — the array of incoming tickets.

### Step 4: Configure the Triage Agent node

1. Inside the for-each loop, select **+ Add node → Agent**.
2. Select **Create new agent**. Name it `TriageAgent` and set instructions:
   ```
   You are a customer support triage specialist for ContosoPay.
   Classify the support ticket as Billing, Technical, or General.
   Return a JSON object with fields: category, confidence (0.0–1.0), and summary.
   ```
3. Set the agent input to `@{items('For_each').description}`.
4. Configure the output format as **JSON** with fields: `category`, `confidence`, `summary`.
5. Save the agent.

### Step 5: Add conditional logic

1. After the Triage Agent node, add a **Condition** node.
2. Set the condition: `@{outputs('TriageAgent').confidence} < 0.7`.
3. In the **True** branch, add a **Set variable** node:
   - Variable: `needsMoreInfo = true`
4. Leave the **False** branch empty (processing continues).

### Step 6: Add the Response Agent node

1. After the conditional, add another **Agent** node.
2. Create `ResponseAgent` with instructions:
   ```
   You are a customer support specialist for ContosoPay.
   Write a professional response for the support ticket that addresses the customer's concern.
   Focus on Technical and General issues only. For Billing issues, direct the customer
   to the billing team.
   ```
3. Set the input to include both the ticket description and the triage summary.
4. Save the node.

### Step 7: Configure the Output node

1. Set the workflow output to return an array of results per ticket:
   ```json
   {
     "ticketId": "@{items('For_each').id}",
     "category": "@{outputs('TriageAgent').category}",
     "confidence": "@{outputs('TriageAgent').confidence}",
     "needsMoreInfo": "@{variables('needsMoreInfo')}",
     "response": "@{outputs('ResponseAgent').content}"
   }
   ```
2. **Save** and **Publish** the workflow.

---

## Part 2 — Invoke the workflow from VS Code

### Step 8: Set up the Python client

1. Clone the repository and navigate to `Labfiles/08-build-workflow-ms-foundry/Python`.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Create a `.env` file:
   ```
   PROJECT_CONNECTION_STRING=<your-connection-string>
   WORKFLOW_NAME=support-ticket-workflow
   ```

### Step 9: Run the workflow client

1. Review the code — it sends a POST request to the Foundry workflow endpoint with a sample array of tickets.
2. Run the script:
   ```bash
   python agent.py
   ```
3. Inspect the output and verify:
   - Each ticket has a category and confidence score.
   - Low-confidence tickets have `needsMoreInfo: true`.
   - Technical and General tickets include a recommended response.

---

## Clean up

Delete the Azure resource group in [https://portal.azure.com](https://portal.azure.com).

## Summary

In this lab you:
- Built a visual sequential workflow in the Foundry portal with a for-each loop, AI agent nodes, and conditional logic.
- Configured two AI agents to classify and respond to support tickets.
- Invoked the completed workflow programmatically from Python using the Foundry SDK.

**Next:** [Advanced Lab 07: Microsoft Agent Framework SDK]({{ '/adv-lab-07-agent-framework.html' | relative_url }})
