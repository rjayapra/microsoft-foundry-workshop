---
layout: page
title: "Advanced Lab 01: Build AI Agents with Portal and VS Code"
nav_order: 10
lab_id: adv-lab-01
category: advanced
---

{% include lab-navigation.html %}

## Lab Summary

Build a complete AI agent solution using both the Microsoft Foundry portal and the Microsoft Foundry VS Code extension. You'll create a basic agent in the portal with grounding data and built-in tools, then interact with it programmatically using VS Code — including code interpreter for data analysis.

## Estimated Time

45 minutes

## Learning Objectives

1. Create and configure an AI agent in the Microsoft Foundry portal.
2. Add grounding data (file search) and enable built-in tools including code interpreter.
3. Use the Microsoft Foundry VS Code extension to work with agents programmatically.
4. Run Python code via the code interpreter to analyse CSV data and generate insights.
5. Understand when to use portal-based vs code-based approaches for agent development.

## Prerequisites

- An Azure subscription with Contributor access and sufficient quota for Azure AI resources.
- Visual Studio Code installed.
- Python 3.12 or later installed.
- Microsoft Foundry VS Code extension installed (v0.16.0 or later).

## Scenario

You'll build an **IT Support Agent** that:
- Answers questions based on IT policy documentation (grounding data via file search).
- Analyses system performance data using code interpreter to identify trends.

---

## Part 1 — Create an agent in the Foundry portal

### Step 1: Create a Foundry project

1. Open [https://ai.azure.com](https://ai.azure.com) and sign in.
2. Select **Start building** in the top banner to use the new Foundry experience.
3. Create a **new project** (e.g. `it-support-agent-project`).
4. Expand **Advanced options** and choose a region, subscription, and resource group.
5. Select **Create** and wait for the project to be provisioned.
6. Select **Start building → Create agent**.
7. Set the **Agent name** to `it-support-agent` and create the agent.

### Step 2: Configure instructions and grounding data

1. In the agent playground, set **Instructions** to:
   ```
   You are a helpful IT support assistant. Use the file search tool to reference the
   IT policy document and answer employee questions about technology guidelines.
   When asked to analyse performance data, use the code interpreter tool to process
   the uploaded CSV file and provide actionable insights.
   ```
2. Under **Tools**, enable **File search**.
3. Create a new vector store named `it-policy-store`.
4. Download [IT_Policy.txt](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-agents/main/Labfiles/01-build-agent-portal-and-vscode/IT_Policy.txt) and upload it to the vector store.
5. Enable **Code interpreter**.
6. Download [system_performance.csv](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-agents/main/Labfiles/01-build-agent-portal-and-vscode/system_performance.csv) and upload it to the code interpreter files.
7. **Save** the agent.

### Step 3: Test in the playground

1. In the chat, try: *"What is the company's policy on BYOD devices?"*
2. Verify the agent references the IT policy document.
3. Try: *"Analyse the system performance data and identify any servers with high CPU usage."*
4. Verify the agent writes and executes code, then summarises the findings.

---

## Part 2 — Interact programmatically from VS Code

### Step 4: Open the lab code in VS Code

1. In the Foundry portal, go to **VS Code** (or use the VS Code extension icon in the sidebar and sign in).
2. Clone the workshop repository:
   ```bash
   git clone https://github.com/rjayapra/microsoft-foundry-workshop.git
   cd microsoft-foundry-workshop
   ```
3. Navigate to `Labfiles/adv-lab-01-build-agent-portal-vscode/Python`.
4. In the terminal, install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
5. Create a `.env` file and set the following values from **Project → Settings** in the Foundry portal:
   ```
   PROJECT_CONNECTION_STRING=<your-connection-string>
   AGENT_ID=<your-agent-id>
   ```

### Step 5: Run the agent client

1. Open `agent_with_functions.py` and review the code structure.
2. Verify the code:
   - Creates an `AIProjectClient` from the connection string.
   - Retrieves the existing agent by ID.
   - Creates a thread, sends a user message, and runs the agent.
   - Polls for the completed run and prints assistant messages.
3. Run the script:
   ```bash
   python agent_with_functions.py
   ```
4. Observe the response in the terminal — the agent should use the uploaded policy and CSV data.

---

## Clean up

If you have finished, delete the Azure resource group to avoid unnecessary charges:

1. Open [https://portal.azure.com](https://portal.azure.com).
2. Navigate to the resource group used for this lab.
3. Select **Delete resource group** and confirm.

## Summary

In this lab you:
- Created an IT Support Agent in the Microsoft Foundry portal with file search and code interpreter tools.
- Tested the agent in the playground using grounding data and data analysis.
- Connected to the same agent from VS Code using the Foundry SDK and ran it programmatically.

**Next:** [Advanced Lab 02: Extend Agents with MCP Tools]({{ '/adv-lab-02-mcp-integration.html' | relative_url }})
