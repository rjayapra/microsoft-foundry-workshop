---
layout: page
title: "Lab 00: Environment Validation"
nav_order: 0
lab_id: lab-00
category: beginner
---

{% include lab-navigation.html %}

## Estimated Time

30 minutes

## Objective

Confirm that you have the access and resources needed before starting the hands-on labs. Everything in this track is done entirely in the browser — no local tools required.

## What you need before starting

- An active **Azure subscription** with at least **Contributor** access to a resource group.
- A browser (Microsoft Edge or Google Chrome recommended).
- Your Azure account credentials ready.

---

## Step 1: Sign in to the Azure portal

1. Open [https://portal.azure.com](https://portal.azure.com) in your browser.
2. Sign in with the account provided for this workshop.
3. In the top search bar, type **Subscriptions** and open the Subscriptions blade.
4. Confirm the workshop subscription is listed and shows a **Active** state.

> **What to check:** You should see the subscription name without any access or policy errors. If you see "No subscriptions found", ask your facilitator to check your account permissions.

**Checkpoint ✅** — You can open the subscription without errors.

---

## Step 2: Create or open the Microsoft Foundry project

Microsoft Foundry is the central hub where you build and manage AI agents. You access it at [https://ai.azure.com](https://ai.azure.com).

1. Open [https://ai.azure.com](https://ai.azure.com) in a new browser tab.
2. Sign in with the same Azure account.
3. If you see a **Welcome to Microsoft Foundry** banner, click **Start building** or **Create project**.

### If no Foundry project exists yet — create one now:

1. Select **+ New project** (or **Create project** from the welcome screen).
2. Enter a **Project name** — for example, `foundry-workshop-yourname`.
3. Expand **Advanced options** and set:
   - **Subscription**: your workshop subscription
   - **Resource group**: use the one provided by your facilitator (or create a new one named `rg-foundry-workshop`)
   - **Region**: use the region recommended by your facilitator (for example, **East US 2** or **Sweden Central**)
4. Select **Create** and wait for the project to be provisioned (this takes 1–3 minutes).
5. Once provisioned, you are taken into the project home page.

> **What to check:** The project home page shows a left navigation with sections like **Agents**, **Models**, and **Knowledge bases**. If provisioning fails, check that your subscription has available quota for Azure AI resources in the selected region.

**Checkpoint ✅** — Foundry project is created and the project home page loads successfully.

---

## Step 3: Deploy a chat model

Agents need a language model to reason and respond. You will deploy one now.

1. In the left navigation, select **Models** (or **Model deployments**).
2. Select **+ Deploy model**.
3. In the model catalog, search for **gpt-5.1** (or any available GPT-5.x model).
4. Select the model and click **Deploy**.
5. On the deployment configuration screen:
   - **Deployment name**: `gpt-5.1` (or keep the default)
   - **Deployment type**: Standard or Global Standard
   - Leave other settings at their defaults
6. Select **Deploy** and wait until the deployment status shows **Succeeded**.
7. Note the **Deployment name** — you will use it when creating agents in later labs.

> **What to check:** The deployment appears in the Models list with a green **Succeeded** status. If you see a quota error, try a different region or ask your facilitator for help.

**Checkpoint ✅** — At least one chat model deployment is healthy and its name is recorded.

---

## Step 4: Explore the Agents section

1. In the left navigation, select **Agents**.
2. Select **+ Create agent**.
3. On the agent creation page, enter any name — for example, `test-agent`.
4. Confirm that the **Model** dropdown shows the deployment you created in Step 3.
5. Select **Create**.
6. You are taken to the **agent playground** for your new agent.
7. In the chat input at the bottom, type: `Hello, can you introduce yourself?`
8. Press **Send** and confirm the agent responds.
9. You can delete this test agent after validation — select the three-dot menu next to the agent name and choose **Delete**.

> **What to check:** The agent responds to your message. If it does not, verify the model deployment is in a healthy state (Step 3).

**Checkpoint ✅** — The agent playground works and the agent responds to a test message.

---

## Step 5: Validate Azure AI Search access (required for Lab 03)

Labs 03 uses a **knowledge base backed by Azure AI Search**. Check whether a Search resource already exists in your subscription, or note that you will create one during Lab 03.

1. In the Azure portal ([https://portal.azure.com](https://portal.azure.com)), search for **AI Search** in the top search bar.
2. Open the **AI Search** blade.
3. Check whether a Search service is listed in your subscription.

> **If a Search resource already exists:** Note the name — you may connect it to Foundry in Lab 03.  
> **If no Search resource exists:** That is fine — you will create one in Lab 03.

**Checkpoint ✅** — You are aware of whether a Search resource exists. No action required yet.

---

## Step 6: Confirm you can upload files in Foundry

Labs 01 and 03 involve uploading files to an agent. Run a quick check now.

1. In [https://ai.azure.com](https://ai.azure.com), navigate to the **Agents** section.
2. Open the test agent you created in Step 4 (or create a new one quickly).
3. Under **Tools**, look for **File search** and click to expand it.
4. Select **+ Add files** or **Create vector store**.
5. Confirm that the file upload dialog opens successfully. You do not need to upload anything yet — just confirm the dialog appears.
6. Close the dialog.

> **What to check:** The upload dialog opens without an error. If you see an access error, ask your facilitator to check your storage permissions.

**Checkpoint ✅** — File upload dialog opens successfully.

---

## Summary

You have confirmed:

| Check | Status |
|---|---|
| Azure subscription is accessible | ✅ |
| Microsoft Foundry project is provisioned | ✅ |
| A chat model deployment is healthy | ✅ |
| Agent playground responds to messages | ✅ |
| Azure AI Search awareness confirmed | ✅ |
| File upload is working | ✅ |

You are ready to start the labs. No Python, no VS Code, and no command line is needed for the beginner track.

**Next:** [Lab 01: Build Your First AI Agent]({{ '/lab-01-first-autonomous-agent.html' | relative_url }})

Checkpoint:

- Local tools are available.

## Exit Criteria

- All platform and local checks pass.
- Participant is ready to begin Lab 01.

{% include lab-navigation.html %}
