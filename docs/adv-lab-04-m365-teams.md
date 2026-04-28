---
layout: page
title: "Advanced Lab 04: Deploy Agents to Microsoft Teams and Copilot"
nav_order: 13
lab_id: adv-lab-04
category: advanced
---

{% include lab-navigation.html %}

## Lab Summary

Publish an AI agent to **Microsoft Teams** and **Microsoft 365 Copilot** so employees can access it where they already work. This lab focuses on the deployment and publishing workflow rather than agent development.

## Estimated Time

40 minutes

## Learning Objectives

1. Create an agent in the Foundry portal with knowledge grounding.
2. Register and configure a Teams App for the agent.
3. Publish the agent to Microsoft Teams.
4. Publish the agent to Microsoft 365 Copilot.
5. Test the deployed agent via Teams and Copilot Chat.

## Prerequisites

- An Azure subscription with Contributor access.
- A Microsoft 365 tenant where you have Teams admin or app-publishing rights.
- Visual Studio Code installed.
- Python 3.12 or later installed.

---

## Step 1: Create and configure the agent

1. Open [https://ai.azure.com](https://ai.azure.com) and navigate to your Foundry project.
2. Go to **Agents → Create agent**.
3. Set the name to `hr-policy-agent` and add instructions:
   ```
   You are an HR policy assistant. Use the knowledge from the uploaded documents
   to answer employee questions accurately and concisely. Direct employees to HR
   if a question requires human judgment.
   ```
4. Enable **File search** and upload the following documents:
   - [it_security_policy.txt](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-agents/main/Labfiles/05a-m365-teams-integration/Python/sample_documents/it_security_policy.txt)
   - [remote_work_policy.txt](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-agents/main/Labfiles/05a-m365-teams-integration/Python/sample_documents/remote_work_policy.txt)
5. Save the agent and test it in the playground.

## Step 2: Set up the environment

1. Clone the workshop repository (if you haven't already):
   ```bash
   git clone https://github.com/rjayapra/microsoft-foundry-workshop.git
   cd microsoft-foundry-workshop
   ```
   Then navigate to `Labfiles/adv-lab-04-m365-teams/Python`.
2. Run the prerequisite check:
   ```bash
   python check_prerequisites.py
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Create a `.env` file with your Foundry project and M365 credentials:
   ```
   PROJECT_ENDPOINT=<your-project-endpoint>
   AGENT_ID=<your-agent-id>
   TENANT_ID=<your-m365-tenant-id>
   CLIENT_ID=<app-registration-client-id>
   CLIENT_SECRET=<app-registration-client-secret>
   ```

## Step 3: Set up Azure AI Search for Teams

1. Run the search setup script:
   ```bash
   python setup_search.py
   ```
2. This script provisions and configures the search index for the agent's knowledge.

## Step 4: Deploy to Microsoft Teams

1. Run the deployment helper:
   ```bash
   python deploy_helper.py --target teams
   ```
2. The script generates a Teams app manifest and registers the bot channel.
3. Follow the output instructions to sideload the app in Teams:
   - Open Teams → **Apps → Manage your apps → Upload a custom app**.
   - Upload the generated `teams-app.zip`.
4. In Teams, open the app and test: *"What is the remote work policy?"*

## Step 5: Publish to Microsoft 365 Copilot

1. Run:
   ```bash
   python deploy_helper.py --target copilot
   ```
2. The script configures the agent as a Copilot plugin.
3. In Microsoft 365 Copilot Chat, type `@hr-policy-agent` and ask a policy question.
4. Verify the response uses your grounded knowledge.

## Step 6: Validate deployment

1. Run the validation script:
   ```bash
   python validate_deployment.py
   ```
2. Review any warnings or errors and resolve them before the session wraps up.

---

## Clean up

1. Run `python cleanup_all.py` to remove app registrations and bot channels.
2. Delete the Azure resource group in [https://portal.azure.com](https://portal.azure.com).

## Summary

In this lab you:
- Created a grounded agent and published it to Microsoft Teams and Microsoft 365 Copilot.
- Used automated deployment scripts to handle app manifest generation and bot channel registration.
- Validated the live deployment from Python.

**Next:** [Advanced Lab 05: Work IQ — Workplace Intelligence]({{ '/adv-lab-05-work-iq.html' | relative_url }})
