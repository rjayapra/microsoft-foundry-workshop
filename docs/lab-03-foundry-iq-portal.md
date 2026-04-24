---
layout: page
title: "Lab 03: Build a Knowledge Base with Foundry IQ"
nav_order: 3
lab_id: lab-03
category: beginner
---

{% include lab-navigation.html %}

## Lab Summary

Create a searchable **knowledge base** from product documents and connect it to an agent using **Foundry IQ** — Microsoft Foundry's built-in knowledge management capability. Everything is done in the portal using Azure AI Search as the indexing backend.

## Estimated Time

45 minutes

## Learning Objectives

1. Create an Azure AI Search resource and connect it to your Foundry project.
2. Build a Foundry IQ knowledge base by uploading product documents.
3. Create an agent that uses the knowledge base to answer questions.
4. Test the agent with product-related queries and validate search quality.

## Scenario

You are building a **Contoso Product Assistant** for a retail company. The agent should help customers find detailed information about outdoor gear — including tents, backpacks, and camping accessories — by searching through a library of product documentation.

---

## What is Foundry IQ?

**Foundry IQ** is Microsoft Foundry's knowledge base feature. It lets you:
- Upload documents (Markdown, PDF, Word, text) and index them.
- Connect the index to an agent so the agent can search across all documents.
- Provide agents with rich, structured knowledge rather than single uploads.

Unlike the **File search** tool from Lab 01 (which works per-agent), Foundry IQ knowledge bases are project-level resources you can reuse across multiple agents.

---

## Step 1: Download the product documents

You need sample product files for this lab. Download them now.

1. Open the following direct download link in your browser:
   - [contoso-products.zip](https://github.com/rjayapra/microsoft-foundry-workshop/raw/main/Labfiles/adv-lab-03-foundry-iq/data/contoso-products.zip)
2. Save the file to your **Downloads** folder.
3. Once downloaded, extract / unzip the archive.
4. Confirm you have these files inside the extracted folder:
   - `contoso-backpacks-guide.md`
   - `contoso-camping-accessories.md`
   - `contoso-tents-catalog.md`
5. Keep this folder open — you will upload these files in Step 3.

**Checkpoint ✅** — Product markdown files are extracted and ready to upload.

---

## Step 2: Create an Azure AI Search resource

Foundry IQ uses **Azure AI Search** to index and search your documents. You need to create a Search resource and connect it to your Foundry project.

> **Already have a Search resource?** If you confirmed one exists during Lab 00, skip to step 2.6 (Connect to your project).

### Create a new Azure AI Search resource:

1. In the Foundry portal ([https://ai.azure.com](https://ai.azure.com)), go to **Settings** in the left navigation (or select your project name and choose **Settings**).
2. Select **Connected resources**.
3. Select **+ New connection**.
4. Choose **Azure AI Search** from the list of resource types.
5. Select **Create a new Azure AI Search resource**.
6. Fill in the details:
   - **Name**: a unique name, for example `search-foundry-workshop` (names must be globally unique, so add your initials or a number)
   - **Pricing tier**: **Basic** (sufficient for this workshop)
   - **Region**: use the **same region** as your Foundry project
   - **Subscription**: your workshop subscription
   - **Resource group**: the same resource group as your Foundry project
7. Select **Review + Create**, then **Create**.
8. Wait for the provisioning to complete (typically 2–3 minutes).

### Connect to your project:

1. Once the Search resource is created, return to **Settings → Connected resources**.
2. Select **+ New connection** again and choose **Azure AI Search**.
3. This time, select the Search resource you just created from the list.
4. Select **Add connection**.
5. Confirm the connection appears in the Connected resources list with a green status.

> **Why is Search needed?** Foundry IQ stores your documents as searchable indexes in Azure AI Search. When an agent queries the knowledge base, it uses Azure AI Search under the hood to find the most relevant document sections. Azure AI Search handles ranking, filtering, and vector similarity search automatically.

**Checkpoint ✅** — Azure AI Search resource is created and connected to your Foundry project.

---

## Step 3: Create the knowledge base

Now create a Foundry IQ knowledge base and upload the product documents.

1. In the left navigation of your Foundry project, select **Knowledge bases** (listed under **Foundry IQ**).
2. Select **+ New knowledge base**.
3. On the creation form, fill in:
   - **Name**: `contoso-products-kb`
   - **Search resource**: select the Azure AI Search resource you connected in Step 2
   - **Embedding model**: select **text-embedding-ada-002** or **text-embedding-3-small** from the dropdown (these are embedding models used to create searchable vectors from your text; either works for this lab)
4. Select **Create**.
5. The knowledge base is now created — you are taken to the knowledge base detail page.

### Upload the product documents:

1. On the knowledge base detail page, select **+ Add files** (or **Upload documents**).
2. Browse to the extracted folder from Step 1.
3. Select all three files:
   - `contoso-backpacks-guide.md`
   - `contoso-camping-accessories.md`
   - `contoso-tents-catalog.md`
4. Select **Upload**.
5. Wait for the indexing to complete — you will see a progress indicator for each file. Indexing typically takes 1–3 minutes per file.
6. Confirm all three files show a **Succeeded** or **Indexed** status.

> **What is indexing?** When you upload a document, Foundry reads the text, splits it into chunks, converts each chunk into vector embeddings (numerical representations), and stores them in Azure AI Search. This makes it possible for the agent to search through hundreds of pages in milliseconds.

**Checkpoint ✅** — All three product documents are indexed in the knowledge base.

---

## Step 4: Create the product assistant agent

1. In the left navigation, select **Agents**.
2. Select **+ Create agent**.
3. Set:
   - **Agent name**: `contoso-product-agent`
   - **Model**: select your deployed model (for example, `gpt-4o`)
4. Select **Create**.
5. On the agent playground, enter the following in the **Instructions** field:

```
You are a knowledgeable product assistant for Contoso outdoor gear.

Your role:
- Answer detailed questions about products including specifications, pricing, and features.
- Use the knowledge base to find accurate product information.
- Always cite the source document name in your answer so the customer knows where the information comes from.
- If a product is not in the knowledge base, say so clearly.

Response style:
- Be friendly and helpful.
- Use bullet points or tables for product comparisons.
- Keep answers focused and relevant to outdoor gear.
```

6. Select **Save**.

**Checkpoint ✅** — Agent is created with instructions.

---

## Step 5: Connect Foundry IQ to the agent

1. In the agent playground, scroll to the **Tools** section.
2. Look for **Foundry IQ** or **Knowledge base** and select it (enable the toggle or click **+ Add**).
3. A dialog appears listing available knowledge bases in your project.
4. Select **contoso-products-kb** (the one you created in Step 3).
5. Select **Add** or **Connect**.
6. Confirm that **contoso-products-kb** appears under Tools with a connected indicator.
7. Select **Save**.

> **What did you just do?** You registered the knowledge base as a tool the agent can call. When a user asks about products, the agent will automatically search the knowledge base and use the top results as context for its answer.

**Checkpoint ✅** — Knowledge base is connected to the agent.

---

## Step 6: Test the agent in the playground

Use the chat panel to test the agent with product questions.

### Test 1 — Basic product lookup

```
What tents does Contoso sell for alpine or high-altitude conditions?
```

**What to look for:**
- The agent should list tents with their key features (waterproofing, weight, packed size, etc.).
- The answer should come from `contoso-tents-catalog.md` — the agent may cite this.
- Information should be specific (actual model names, specs), not generic.

### Test 2 — Product comparison

```
Compare the top two backpacks from Contoso. Which one is better for long multi-day hikes?
```

**What to look for:**
- The agent should compare two specific backpacks with real attributes.
- It may produce a comparison table or bullet-point list.
- It should make a recommendation based on the specs, not a generic guess.

### Test 3 — Accessories question

```
What camping accessories does Contoso sell for cooking and food preparation?
```

**What to look for:**
- Response should reference `contoso-camping-accessories.md`.
- Specific product names, weights, or materials should appear.

### Test 4 — Out-of-scope question (boundary test)

```
Does Contoso sell kayaks or water sports equipment?
```

**What to look for:**
- The agent should say it does not have information about this in the knowledge base.
- It should **not** make up products that do not exist in the documents.
- This validates that the agent stays grounded in your data.

**Checkpoint ✅** — Agent answers all four test prompts correctly, citing documents and not inventing data.

---

## Understanding knowledge base search quality

If agent responses seem inaccurate or miss obvious information, try these adjustments:

| Symptom | Likely cause | Fix |
|---|---|---|
| Agent invents product names | Knowledge base not properly connected | Verify Foundry IQ appears in Tools section |
| Agent says "no information found" | Indexing not complete | Wait for all files to show Succeeded status |
| Agent gives generic answers | Instructions don't mention knowledge base | Update instructions to explicitly say "use the knowledge base" |
| Missing specific specs | Specs are in a section the chunker missed | Nothing to do in portal; content quality affects results |

---

## Compare: File search vs Foundry IQ

| Feature | **File search (Lab 01)** | **Foundry IQ (Lab 03)** |
|---|---|---|
| **Scope** | Tied to one agent | Project-level, reusable across agents |
| **Scale** | Best for a few small files | Designed for large document libraries |
| **Backend** | Foundry internal storage | Azure AI Search |
| **Control** | Minimal | Full index management through Search |
| **Setup** | Upload files to agent | Create knowledge base, connect to Search, then connect to agent |
| **Best for** | Quick agent-specific grounding | Enterprise knowledge management |

---

## Clean up (optional)

If you want to clean up resources at the end of the workshop:

1. Delete the agent: **Agents → contoso-product-agent → Delete**.
2. Delete the knowledge base: **Knowledge bases → contoso-products-kb → Delete**.
3. The Azure AI Search resource can be deleted from the Azure portal when you are done with all labs.

---

## Summary

In this lab you:
- Created an Azure AI Search resource and connected it to your Foundry project.
- Built a Foundry IQ knowledge base from three product documentation files.
- Configured a product assistant agent to search the knowledge base.
- Tested the agent with product queries, comparisons, and boundary tests.

**Next:** [Lab 04: Multi-Agent Orchestration Concepts]({{ '/lab-04-multi-agent-portal.html' | relative_url }})

{% include lab-navigation.html %}
