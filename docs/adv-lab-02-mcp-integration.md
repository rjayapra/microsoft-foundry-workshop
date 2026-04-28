---
layout: page
title: "Advanced Lab 02: Extend Agents with MCP Tools"
nav_order: 11
lab_id: adv-lab-02
category: advanced
---

{% include lab-navigation.html %}

## Lab Summary

Extend agent capabilities by integrating **Model Context Protocol (MCP)** server tools. You'll connect an agent to a remote MCP server hosted by Microsoft (Learn Docs) and also build a custom local MCP server — enabling the agent to retrieve real-time external information.

## Estimated Time

60 minutes

## Learning Objectives

1. Install and configure the Microsoft Foundry VS Code extension.
2. Create a Foundry project and deploy a model from VS Code.
3. Connect an agent to a remote cloud-hosted MCP server.
4. Build a custom local MCP server and expose it to the agent.
5. Interact with and test the MCP-enabled agent from Python code.

## Prerequisites

- Visual Studio Code installed.
- An active Azure subscription.
- Python 3.10 or later installed.
- Microsoft Foundry VS Code extension installed (v0.16.0 or later).

---

## Step 1: Install the Microsoft Foundry VS Code extension

1. Open VS Code and press **Ctrl+Shift+X** to open Extensions.
2. Search for **Microsoft Foundry** and install the extension from Microsoft.
3. After installation, confirm the Foundry icon appears in the primary sidebar.

## Step 2: Sign in to Azure and create a project

1. In the Foundry sidebar, select **Sign in to Azure** and complete authentication.
2. Select the **+** icon next to **Resources** to create a new Foundry project.
3. Choose your subscription, a resource group (existing or new), and a region.
4. Enter a project name (e.g. `ai-agents-project`) and wait for deployment.

## Step 3: Deploy a model

1. When the "Project deployed successfully" popup appears, select **Deploy a model**.
2. In the Model Catalog, locate **gpt-5.1** and select **Deploy**.
3. Use *Global Standard* or *Standard* deployment type and accept default settings.
4. Wait for the model to deploy and appear under **Models** in the sidebar.

## Step 4: Connect the agent to a remote MCP server

1. Clone the workshop repository (if you haven't already):
   ```bash
   git clone https://github.com/rjayapra/microsoft-foundry-workshop.git
   cd microsoft-foundry-workshop
   ```
   Then navigate to `Labfiles/adv-lab-02-mcp-integration/Python`.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Open `agent.py` and review the MCP configuration — the agent connects to:
   ```
   https://learn.microsoft.com/api/mcp
   ```
4. Create a `.env` file with your Foundry project connection string:
   ```
   PROJECT_ENDPOINT=<your-project-endpoint>
   ```
5. Run the agent:
   ```bash
   python agent.py
   ```
6. Enter a question such as: *"What is the latest documentation for Azure AI Agent Service?"*
7. Verify the agent retrieves real-time results from Microsoft Docs via the MCP tool.

## Step 5: Run the custom local MCP server

1. In the same directory, open `server.py`.
2. The server implements a simple MCP tool — review the `@mcp.tool()` decorated function.
3. Start the local server:
   ```bash
   python server.py
   ```
4. In a second terminal, open `client.py` and update the `server_url` to point to your local server (e.g. `http://localhost:8000/mcp`).
5. Run the client:
   ```bash
   python client.py
   ```
6. Verify the agent can call the custom tool and return locally-served data.

---

## Clean up

Delete the Azure resource group in [https://portal.azure.com](https://portal.azure.com) to avoid charges.

## Summary

In this lab you:
- Connected an agent to the Microsoft Learn Docs MCP server to fetch real-time documentation.
- Built and exposed a custom local MCP server.
- Used the Foundry SDK Python client to interact with MCP-enabled agents.

**Next:** [Advanced Lab 03: Integrate Agent with Foundry IQ]({{ '/adv-lab-03-foundry-iq.html' | relative_url }})
