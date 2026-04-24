---
layout: page
title: "Lab 02: Extend Your Agent with MCP Tools"
nav_order: 2
lab_id: lab-02
category: beginner
---

{% include lab-navigation.html %}

## Lab Summary

Extend your agent's capabilities by connecting it to external tools using the **Model Context Protocol (MCP)**. You will connect your agent to a live MCP server — the Microsoft Learn documentation service — entirely through the Foundry portal. No coding required.

## Estimated Time

30 minutes

## Learning Objectives

1. Understand what MCP is and why it matters for agents.
2. Connect an agent to a remote MCP server in the Foundry portal.
3. Test the agent's ability to retrieve real-time information through the MCP tool.
4. Understand the difference between grounding documents (static) and MCP tools (live).

## Background: What is MCP?

**MCP (Model Context Protocol)** is an open standard that lets AI agents call external tools and services — like databases, APIs, or documentation systems — in a structured and secure way.

Think of it like giving your agent a phone book of tools it can call. When a user asks a question that needs live or external information, the agent knows which tool to call, what to send, and how to interpret the response.

In this lab, you will connect your agent to the **Microsoft Learn Docs MCP server** — a live service that lets the agent search [https://learn.microsoft.com](https://learn.microsoft.com) in real time.

---

## Step 1: Open or create your agent

1. Open [https://ai.azure.com](https://ai.azure.com) and navigate to your Foundry project.
2. In the left navigation, select **Agents**.
3. You can either:
   - **Continue with the agent from Lab 01** (`it-support-agent`) — select it to open it in the playground.
   - Or create a new agent: select **+ Create agent**, name it `docs-agent`, select your model deployment, and click **Create**.

**Checkpoint ✅** — Your agent is open in the playground.

---

## Step 2: Add an MCP server connection

1. In the agent playground, scroll to the **Tools** section on the left panel.
2. Look for **MCP servers** or **+ Add tool** — the exact label depends on your portal version.
3. Select **+ Add MCP server** (or press **+ Add tool** and choose **MCP server** from the dropdown).
4. A dialog opens asking for the MCP server URL. Enter the following:
   ```
   https://learn.microsoft.com/api/mcp
   ```
5. Leave the **Authentication** setting as **None** (this is a public MCP server — no key required).
6. Select **Connect** (or **Add**).
7. Wait a moment for the portal to connect and discover the tools provided by this server.
8. You should see a list of tools appear — such as `search_documentation` or similar tool names.
9. Confirm the MCP connection is listed under Tools with a green connected indicator.
10. Select **Save**.

> **What just happened?** Foundry contacted the MCP server and asked it: *"What tools do you offer?"* The server returned a list of available functions (like search), and Foundry registered them with your agent. Now the agent knows it can call these tools whenever a user asks a question that needs live documentation.

**Checkpoint ✅** — MCP server is connected and tools are visible.

---

## Step 3: Understand the MCP tool that was added

Before testing, take a moment to explore what tool was connected.

1. In the Tools section, select the MCP tool to expand its details.
2. You should see a **tool name** (for example, `search_documentation`) and a **description** explaining what it does.
3. The description might say something like: *"Searches learn.microsoft.com documentation for the given query."*

> **Why does the description matter?** The agent uses the tool description to decide *when* to use this tool. If a user asks about Azure services, the agent reads the description and understands that this MCP tool can help. The description is the agent's guide to choosing the right tool.

**Checkpoint ✅** — You can see the MCP tool name and description.

---

## Step 4: Update the agent's instructions

To guide the agent to use the MCP tool effectively, update its instructions.

1. In the **Instructions** field, scroll to the top or select **Edit instructions**.
2. Add the following at the end of your existing instructions (or replace them if starting fresh):

```
You are a helpful AI assistant that answers questions about Microsoft products and Azure services.

When a user asks about Microsoft documentation, Azure features, or technical how-to questions:
- Use the MCP search tool to retrieve the latest documentation from learn.microsoft.com.
- Always summarise the results in plain language.
- Include a link to the relevant documentation page when possible.

If the user asks about Contoso IT policies or server data, refer to the files in your File search or Code interpreter tools.
```

3. Select **Save**.

**Checkpoint ✅** — Instructions are updated to guide MCP tool usage.

---

## Step 5: Test the MCP-connected agent

Use the chat panel on the right side to test the agent.

### Test 1 — Live documentation search

Type the following and press **Send**:

```
What is Azure AI Agent Service and what are its key capabilities?
```

**What to look for:**
- The agent should indicate it is searching documentation (you may see a tool call indicator).
- The response should be accurate and up-to-date — describing Azure AI Agent Service features.
- Ideally the response includes a link to learn.microsoft.com.

### Test 2 — Specific technical question

Type the following and press **Send**:

```
How do I create a knowledge base in Microsoft Foundry?
```

**What to look for:**
- The agent searches the docs and returns relevant steps.
- The content should be more specific than a generic language model answer because it is sourced from actual documentation.

### Test 3 — Compare MCP vs general knowledge

Type the following and press **Send**:

```
What was announced in the latest Microsoft Ignite conference for Azure AI?
```

**What to look for:**
- The agent uses the MCP tool to search for recent announcements.
- The response should be specific and reference actual documentation pages.

> **Tip:** If the agent responds without calling the tool (i.e., gives a generic language model answer), try making your instructions more explicit: *"Always use the search documentation tool before answering questions about Microsoft products."*

**Checkpoint ✅** — Agent successfully retrieves live documentation using the MCP tool.

---

## Understanding the difference: Documents vs MCP tools

| | **File search (Lab 01)** | **MCP tools (Lab 02)** |
|---|---|---|
| **Data source** | Files you uploaded to the vector store | Live external service (API or web) |
| **Content freshness** | Fixed at upload time | Real-time |
| **Setup** | Upload files, create vector store | Enter MCP server URL |
| **Best for** | Internal documents, policies, fixed reference data | Live documentation, APIs, search, databases |
| **Agent decision** | Agent searches your files | Agent calls an external tool |

---

## Common issues

| Problem | Solution |
|---|---|
| MCP server URL returns an error | Check the URL is exactly `https://learn.microsoft.com/api/mcp` — no trailing slash |
| No tools appear after connecting | The server may be temporarily unavailable; try again after 1 minute |
| Agent does not call the MCP tool | Update instructions to explicitly direct the agent to use search for documentation questions |
| Agent says "I cannot browse the internet" | This means MCP is not connected — verify the tool appears under Tools with a green indicator |

---

## Step 6: Explore (optional) — Disable MCP and compare

To see the difference the MCP tool makes:

1. Temporarily disable the MCP tool by toggling it off in the Tools section.
2. Ask the same question: *"What is Azure AI Agent Service and what are its key capabilities?"*
3. Compare the response — it will be based on the model's training data, not live documentation.
4. Re-enable the MCP tool.

This shows you the value of connecting agents to live tool sources.

---

## Summary

In this lab you:
- Understood what MCP is and how it extends agent capabilities with live external tools.
- Connected your agent to the Microsoft Learn Docs MCP server in the Foundry portal.
- Tested the agent retrieving real-time documentation through an MCP tool.
- Compared static document grounding (File search) with live tool access (MCP).

**Next:** [Lab 03: Build a Knowledge Base with Foundry IQ]({{ '/lab-03-foundry-iq-portal.html' | relative_url }})

{% include lab-navigation.html %}
