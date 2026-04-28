---
layout: page
title: "Lab 01: Build Your First AI Agent"
nav_order: 1
lab_id: lab-01
category: beginner
---

{% include lab-navigation.html %}

## Lab Summary

Build a complete AI agent entirely in the **Microsoft Foundry portal** — no coding required. You will create an IT Support Agent that answers questions from a policy document and analyses performance data using the built-in code interpreter tool.

## Estimated Time

45 minutes

## Learning Objectives

1. Create and configure an AI agent in the Microsoft Foundry portal.
2. Write clear instructions that guide agent behaviour.
3. Attach grounding documents using the **File search** tool.
4. Enable the **Code interpreter** tool for data analysis.
5. Test the agent in the Foundry playground and validate responses.

## Scenario

You are building an **IT Support Agent** for Contoso. The agent should:
- Answer employee questions by searching an IT policy document.
- Analyse server performance data from a CSV file and identify problems.

---

## Step 1: Open your Foundry project

1. Open [https://ai.azure.com](https://ai.azure.com) and sign in.
2. Select the project you created in Lab 00 (for example, `foundry-workshop-yourname`).
3. You should see the project home page with the left navigation showing **Agents**, **Models**, and other sections.

> **New to Foundry?** The left navigation is your main control panel. **Agents** is where you build and test AI assistants. **Models** is where you manage language model deployments.

**Checkpoint ✅** — Project home page is open.

---

## Step 2: Download the lab files

You need two sample files for this lab. Download them now:

1. Right-click the link below and choose **Save link as** to download:
   - [IT_Policy.txt](https://github.com/rjayapra/microsoft-foundry-workshop/raw/main/Labfiles/adv-lab-01-build-agent-portal-vscode/IT_Policy.txt) — the IT policy document your agent will search.
   - [system_performance.csv](https://github.com/rjayapra/microsoft-foundry-workshop/raw/main/Labfiles/adv-lab-01-build-agent-portal-vscode/system_performance.csv) — server performance data for analysis.
2. Save both files to your **Downloads** folder (or any location you can easily find).

**Checkpoint ✅** — Both files are saved to your computer.

---

## Step 3: Create the agent

1. In the left navigation, select **Agents**.
2. Select **+ Create agent**.
3. On the agent creation page:
   - **Agent name**: `it-support-agent`
   - **Model**: select the model deployment you confirmed in Lab 00 (for example, `gpt-5.1`)
4. Select **Create**.
5. You are taken to the **Agent playground** — this is where you will configure and test the agent.

> **What is the playground?** The playground lets you configure the agent's instructions and tools on the left side, and chat with it on the right side. Changes you make on the left take effect immediately when you test on the right.

**Checkpoint ✅** — Agent is created and the playground is open.

---

## Step 4: Write the agent's instructions

Instructions tell the agent who it is, what it should do, and how it should behave. Good instructions lead to reliable, predictable responses.

1. In the playground, find the **Instructions** text box on the left side (sometimes labelled **System message**).
2. Clear any existing text and paste the following:

```
You are a helpful IT support assistant for Contoso employees.

Your responsibilities:
1. Answer questions about company IT policies by searching the uploaded policy document.
2. Analyse server performance data using the code interpreter when asked about system health.

Guidelines:
- Always cite the source document when answering policy questions.
- When analysing data, write and run code to calculate statistics or find anomalies.
- If you cannot find an answer in the documents, say so clearly rather than guessing.
- Keep answers concise and actionable.
```

3. Select **Save** (or **Apply**) to save the instructions.

> **Why do instructions matter?** Without instructions, the agent responds as a general assistant. Instructions constrain the agent to your scenario, making it more accurate and reliable for your users.

**Checkpoint ✅** — Instructions are saved.

---

## Step 5: Add grounding documents with File search

The **File search** tool lets the agent search through documents you upload and use the content to answer questions. This is called *grounding* — the agent grounds its answers in real documents rather than guessing.

1. In the playground, scroll down in the left panel to find the **Tools** section.
2. Select **File search** (click the toggle to enable it, or click **+ Add** next to File search).
3. A panel opens asking you to create or select a **Vector store**. A vector store is where Foundry indexes your documents for fast search.
4. Select **+ Create new vector store**.
5. Enter a name: `it-policy-store`.
6. Select **Create**.
7. Once the vector store is created, select **+ Add files** (or **Upload files**).
8. Browse to your Downloads folder and upload `IT_Policy.txt`.
9. Wait for the upload and indexing to complete — you will see a status indicator.
10. Select **Save** when done.

> **What is a vector store?** Foundry converts your documents into a special numerical format (vectors) that the agent can search very quickly. This makes it possible to find relevant sections in large documents instantly.

**Checkpoint ✅** — `IT_Policy.txt` is uploaded and indexed in the vector store.

---

## Step 6: Enable the Code interpreter tool

The **Code interpreter** tool lets the agent write and run Python code to analyse data files. You do not need to write any code yourself — the agent does that automatically.

1. In the **Tools** section, find **Code interpreter** and click to enable it.
2. Select **+ Add files** next to Code interpreter.
3. Upload `system_performance.csv` from your Downloads folder.
4. Wait for the upload to complete.
5. Select **Save**.

> **How does Code interpreter work?** When you ask the agent to analyse the CSV file, it automatically writes Python code, runs it in a secure sandbox, and gives you the results in plain language. You only see the final answer — not the code (unless you ask to see it).

**Checkpoint ✅** — Code interpreter is enabled and `system_performance.csv` is uploaded.

---

## Step 7: Test the agent in the playground

Now test the agent to confirm both tools are working. Use the chat input on the right side of the playground.

### Test 1 — Policy document search

Type the following in the chat and press **Send**:

```
What is the company's policy on using personal devices (BYOD) for work?
```

**What to look for in the response:**
- The agent should answer using information from `IT_Policy.txt`.
- It should reference or cite the document (for example, mentioning a section or quoting a policy rule).
- It should NOT make up a policy that isn't in the document.

If the agent responds with "I don't have information about this", scroll back and check that File search is enabled and the file was indexed successfully.

### Test 2 — Data analysis with Code interpreter

Type the following in the chat and press **Send**:

```
Analyse the server performance data and identify any servers with unusually high CPU usage.
```

**What to look for in the response:**
- The agent should mention that it is running code to analyse the data.
- It should list specific servers with high CPU usage with their values.
- The answer should look data-driven, not generic.

> **Tip:** You can click **Show code** (if visible) to see the Python code the agent wrote and ran. This is a useful way to understand what analysis was performed.

### Test 3 — Combined scenario

Type the following and press **Send**:

```
Based on the IT policy, what actions should I take for servers that are exceeding performance thresholds?
```

**What to look for:** The agent should combine knowledge from both the policy document and the data analysis to give a contextual answer.

**Checkpoint ✅** — Agent responds correctly to all three test prompts.

---

## Understanding what you built

| Component | What it does |
|---|---|
| **Agent instructions** | Define the agent's role, purpose, and behaviour guidelines |
| **File search tool** | Lets the agent search your uploaded documents and cite content |
| **Vector store** | Indexes documents so the agent can search them quickly |
| **Code interpreter tool** | Lets the agent write and run code to analyse data files |
| **Playground** | Interactive environment to test and refine your agent |

---

## Troubleshooting

| Problem | Solution |
|---|---|
| Agent doesn't reference the policy document | Check that File search is enabled and the file shows as indexed |
| Agent says it cannot analyse the CSV | Check that Code interpreter is enabled and the CSV was uploaded |
| Agent gives generic answers | Review your instructions — make sure they explicitly mention the tools and when to use them |
| Model not available in dropdown | Return to Lab 00 and verify your model deployment is healthy |

---

## Clean up (optional)

If you are done with this lab and do not need the agent, you can delete it:

1. In the left navigation, select **Agents**.
2. Find `it-support-agent` and select the three-dot menu (**...**).
3. Select **Delete** and confirm.

> You do **not** need to delete the vector store or model deployment — they will be used in later labs or cleaned up at the end of the workshop.

---

## Summary

In this lab you:
- Created an IT Support Agent in the Microsoft Foundry portal.
- Wrote instructions to define the agent's role and behaviour.
- Attached a policy document using the File search tool.
- Uploaded performance data for the Code interpreter tool.
- Tested the agent in the playground using grounding data and data analysis.

**Next:** [Lab 02: Extend Your Agent with MCP Tools]({{ '/lab-02-mcp-tools-portal.html' | relative_url }})

{% include lab-navigation.html %}
