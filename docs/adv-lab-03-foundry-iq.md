---
layout: page
title: "Advanced Lab 03: Integrate Agent with Foundry IQ"
nav_order: 12
lab_id: adv-lab-03
category: advanced
---

{% include lab-navigation.html %}

## Lab Summary

Use **Azure AI Foundry** and **Foundry IQ** to build an agent that searches a knowledge base of product documentation. You'll provision a search resource, ingest product data, configure the agent in the portal, and then interact with it programmatically using the Foundry SDK from VS Code.

## Estimated Time

45 minutes

## Learning Objectives

1. Create a Foundry project using the new Foundry experience.
2. Provision an Azure AI Search resource for Foundry IQ.
3. Create a knowledge base from product documentation files.
4. Build and configure an agent that searches the knowledge base.
5. Connect to the agent from VS Code using the Foundry Python SDK.

## Prerequisites

- An Azure subscription with Contributor access.
- Visual Studio Code installed.
- Python 3.12 or later installed.

---

## Step 1: Create a Foundry project

1. Open [https://ai.azure.com](https://ai.azure.com) and sign in.
2. Ensure the **New Foundry** toggle is **On**.
3. Select **Create agent** from the home page.
4. Enter a project name and configure the subscription, resource group, and a recommended region.
5. Select **Create** and wait for the project to be provisioned.

## Step 2: Create an Azure AI Search resource

1. In the Foundry portal, go to **Project → Settings → Connected resources**.
2. Select **+ New connection** and choose **Azure AI Search**.
3. Select **Create a new Azure AI Search resource** and configure it:
   - **Name**: a unique name (e.g. `foundry-search-xxxxxxxx`)
   - **Pricing tier**: Basic or Standard S1
   - **Region**: same as your Foundry project
4. Select **Create** and wait for provisioning to complete.
5. Connect the new search resource to your project.

## Step 3: Create a knowledge base

1. Download the sample product files:
   - [contoso-products.zip](https://github.com/MicrosoftLearning/mslearn-ai-agents/raw/main/Labfiles/09-integrate-agent-with-foundry-iq/data/contoso-products.zip)
2. Extract the archive — it contains product information markdown files (tents, backpacks, etc.).
3. In the Foundry portal, go to **Knowledge bases** (under Foundry IQ) and select **+ New knowledge base**.
4. Set:
   - **Name**: `contoso-products-kb`
   - **Search resource**: the resource you created in Step 2
   - **Embedding model**: `text-embedding-ada-002` (or equivalent)
5. Upload all the extracted markdown files from `contoso-products.zip`.
6. Wait for indexing to complete (this may take several minutes).

## Step 4: Build and configure the agent

1. In the Foundry portal, go to **Agents** and select **Create agent**.
2. Set:
   - **Name**: `contoso-product-agent`
   - **Instructions**: 
     ```
     You are a knowledgeable product assistant for Contoso outdoor gear.
     Use the knowledge base to answer detailed questions about products including
     specifications, pricing, and features. Always cite the source document.
     ```
3. Under **Tools**, enable **Foundry IQ** and connect it to `contoso-products-kb`.
4. Test the agent in the playground:
   - *"What tents does Contoso sell for alpine conditions?"*
   - *"Compare the Summit Pro 3000 backpack with the TrailMaster X500."*

## Step 5: Connect from VS Code using the Foundry SDK

1. Clone the workshop repository (if you haven't already):
   ```bash
   git clone https://github.com/rjayapra/microsoft-foundry-workshop.git
   cd microsoft-foundry-workshop
   ```
   Then navigate to `Labfiles/adv-lab-03-foundry-iq/Python`.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Create a `.env` file with values from **Project → Settings**:
   ```
   PROJECT_CONNECTION_STRING=<your-connection-string>
   AGENT_ID=<your-agent-id>
   ```
4. Review `agent.py` — note how the SDK creates a thread, submits a message, and polls for the result.
5. Run the script:
   ```bash
   python agent.py
   ```
6. Verify the agent returns product information sourced from the knowledge base.

---

## Clean up

Delete the Azure resource group in [https://portal.azure.com](https://portal.azure.com) to avoid charges.

## Summary

In this lab you:
- Created a Foundry IQ knowledge base backed by Azure AI Search.
- Ingested product documentation and configured an agent to search it.
- Connected to the agent from Python using the Foundry SDK.

**Next:** [Advanced Lab 04: Deploy Agents to Microsoft Teams and Copilot]({{ '/adv-lab-04-m365-teams.html' | relative_url }})
