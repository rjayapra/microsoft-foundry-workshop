---
layout: page
title: "Lab 04: Multi-Agent Orchestration Concepts"
nav_order: 4
lab_id: lab-04
category: beginner
---

{% include lab-navigation.html %}

## Lab Summary

Learn the concept of **multi-agent orchestration** by building three specialised agents in the Foundry portal and simulating a sequential pipeline manually. You will pass the output of one agent as the input to the next — experiencing first-hand how agents with focused roles outperform a single general-purpose agent.

## Estimated Time

35 minutes

## Learning Objectives

1. Understand why multi-agent systems are more effective than single-agent systems for complex tasks.
2. Create three specialised agents with distinct, focused roles.
3. Simulate a sequential orchestration pipeline manually in the playground.
4. Understand how this pattern is automated with code in advanced labs.

## Background: Why multi-agent?

A single agent asked to do many things often produces mediocre results — it tries to summarise *and* classify *and* recommend, and none of those tasks is done with full focus.

**Multi-agent systems** split complex work into stages. Each agent:
- Has a single, clear purpose.
- Receives focused input.
- Produces a clean output for the next stage.

This is exactly how professional teams work: one person gathers data, another analyses it, a third makes recommendations.

### The pipeline you will build

You will process **customer product feedback** through three stages:

```
Raw customer feedback
       ↓
 [Summariser Agent] → One-sentence neutral summary
       ↓
 [Classifier Agent] → Category: Positive / Negative / Feature Request
       ↓
 [Action Agent]    → Specific recommended action for the support team
```

---

## Step 1: Create the Summariser Agent

1. Open [https://ai.azure.com](https://ai.azure.com) and navigate to your Foundry project.
2. In the left navigation, select **Agents**.
3. Select **+ Create agent**.
4. Set:
   - **Agent name**: `summariser-agent`
   - **Model**: your deployed model (for example, `gpt-4o`)
5. Select **Create**.
6. In the **Instructions** field, enter:

```
Your only job is to summarise customer feedback in exactly one sentence.

Rules:
- Write exactly one sentence.
- Be neutral — do not add opinions, judgements, or analysis.
- Capture the key point of the feedback accurately.
- Do not start with "The customer says" or similar phrases.
- Output only the summary sentence, nothing else.
```

7. Select **Save**.

**Checkpoint ✅** — Summariser Agent is created with focused, single-purpose instructions.

---

## Step 2: Create the Classifier Agent

1. Select **+ Create agent** again.
2. Set:
   - **Agent name**: `classifier-agent`
   - **Model**: your deployed model
3. Select **Create**.
4. In the **Instructions** field, enter:

```
Your only job is to classify customer feedback summaries into one of three categories.

Categories:
- Positive — the feedback expresses satisfaction, praise, or a good experience.
- Negative — the feedback expresses a problem, complaint, disappointment, or frustration.
- Feature Request — the feedback asks for a new capability, improvement, or addition.

Rules:
- Respond with exactly one word: Positive, Negative, or Feature Request.
- Do not add explanations, reasoning, or additional text.
- If the feedback could fit two categories, choose the most dominant one.
```

5. Select **Save**.

**Checkpoint ✅** — Classifier Agent is created.

---

## Step 3: Create the Action Recommender Agent

1. Select **+ Create agent** again.
2. Set:
   - **Agent name**: `action-recommender-agent`
   - **Model**: your deployed model
3. Select **Create**.
4. In the **Instructions** field, enter:

```
Your job is to recommend a specific, actionable next step for the support team based on:
1. A one-sentence summary of customer feedback.
2. The category of that feedback (Positive, Negative, or Feature Request).

Rules:
- Recommend exactly one action.
- Be specific — name a real step the team should take, not a vague suggestion.
- Keep the recommendation to one or two sentences.
- Follow these patterns:
  - Negative → escalate, contact customer, offer resolution
  - Feature Request → log in backlog, tag for product team, vote count
  - Positive → thank customer, share with team, consider for testimonial

Output only the recommended action text.
```

5. Select **Save**.

**Checkpoint ✅** — All three agents are created and visible in the Agents list.

---

## Step 4: Run a sample through the pipeline manually

You will now manually chain the three agents together in their playgrounds — copying the output of each agent and pasting it as input to the next. This simulates what the programmable pipeline does automatically.

Use this sample customer feedback (copy it exactly):

> *"I've been waiting three weeks for my order to arrive and every time I contact support I get a different answer about the status. Nobody seems to know what's happening with my package and it's very frustrating."*

---

### Stage 1: Summarise the feedback

1. Open the **summariser-agent** playground (click the agent name in the Agents list).
2. In the chat input, paste the raw feedback above (the full paragraph).
3. Press **Send**.
4. The agent should return a single neutral sentence summary. Example output:
   > *"Customer reports a delayed order with inconsistent support responses causing frustration."*
5. **Copy this summary sentence** — you will use it in Stage 2.

---

### Stage 2: Classify the summary

1. Open the **classifier-agent** playground.
2. Paste the summary sentence from Stage 1 into the chat input.
3. Press **Send**.
4. The agent should return exactly one word. Example output:
   > *"Negative"*
5. **Copy the category word** — you will use it in Stage 3.

---

### Stage 3: Recommend an action

1. Open the **action-recommender-agent** playground.
2. Paste the following into the chat input, replacing the placeholders with the outputs from Stages 1 and 2:

```
Summary: [paste the summary from Stage 1 here]
Category: [paste the category from Stage 2 here]
```

For example:
```
Summary: Customer reports a delayed order with inconsistent support responses causing frustration.
Category: Negative
```

3. Press **Send**.
4. The agent should return a specific action. Example output:
   > *"Escalate the case to a senior support agent and proactively contact the customer with a definitive delivery timeline and compensation offer."*

**Checkpoint ✅** — You successfully ran three-stage feedback processing pipeline manually.

---

## Step 5: Try a second feedback sample

Repeat the pipeline with this second sample to see different outputs:

> *"I absolutely love the new backpack! The strap design is incredibly comfortable, and the waterproof compartment saved my laptop during a rainstorm. Would be amazing if it also had a solar charging panel on the back."*

Run it through all three stages and record the outputs.

| Stage | Expected output type |
|---|---|
| Summariser | One neutral sentence |
| Classifier | `Feature Request` (dominant theme) |
| Action Recommender | Log the solar charging feature in the product backlog |

**Checkpoint ✅** — Second sample produces a different classification and action.

---

## Step 6: Reflect — What did you notice?

Take a moment to think about the experience. Discussion questions:

1. **Why one sentence in Stage 1?** If the summariser sent the full raw feedback to the classifier, would the classification be as reliable?

2. **Why not combine Stage 1 and Stage 2 into one agent?** Try asking a single agent: *"Summarise and classify this feedback in one response: [paste the raw feedback]."* Compare the output quality.

3. **What would break if the Summariser added opinions?** For example: *"Angry customer complains about bad shipping."* How would that bias the Classifier?

> **Key insight:** Each agent in the pipeline has a **constraint** — it must do exactly one thing and produce clean output. This constraint is what makes multi-agent pipelines reliable. Ambiguity compounds at each stage, so keeping each step precise keeps the whole pipeline accurate.

---

## How this maps to the programmable version (Advanced Lab 08)

In **Advanced Lab 08**, developers automate this exact pipeline using Python and the Microsoft Agent Framework SDK:

```
[Python script]
   → creates all three agents via the SDK
   → runs Stage 1: feeds raw feedback to summariser-agent
   → runs Stage 2: feeds summary to classifier-agent
   → runs Stage 3: feeds summary + category to action-recommender-agent
   → prints the full chained output
```

The agents you created here are identical in concept. The difference is that the SDK automates the copy-paste steps and can process hundreds of feedback items in minutes.

---

## Clean up (optional)

1. Select each agent in the Agents list.
2. Choose **Delete** from the three-dot menu.
3. Repeat for all three agents.

---

## Summary

In this lab you:
- Learned why multi-agent systems with specialised roles outperform single general-purpose agents.
- Created three focused agents: Summariser, Classifier, and Action Recommender.
- Simulated a sequential orchestration pipeline manually in the Foundry playground.
- Observed how clean, constrained outputs from each stage enable reliable downstream reasoning.

---

## You have completed the beginner lab track!

| Lab | Topic | Status |
|---|---|---|
| Lab 00 | Environment Validation | ✅ |
| Lab 01 | Build Your First AI Agent | ✅ |
| Lab 02 | Extend with MCP Tools | ✅ |
| Lab 03 | Build a Knowledge Base with Foundry IQ | ✅ |
| Lab 04 | Multi-Agent Orchestration Concepts | ✅ |

---

## Where to go next

Ready to go deeper? The **Advanced Labs** automate everything you did manually and introduce programmatic agent development with Python and the Foundry SDK.

- [Advanced Lab 01: Build AI Agents with Portal and VS Code]({{ '/adv-lab-01-build-agent-portal-vscode.html' | relative_url }}) — the same agent from Lab 01, extended with Python
- [Advanced Lab 02: Extend Agents with MCP Tools]({{ '/adv-lab-02-mcp-integration.html' | relative_url }}) — build a custom local MCP server
- [Advanced Lab 03: Integrate Agent with Foundry IQ]({{ '/adv-lab-03-foundry-iq.html' | relative_url }}) — interact with the knowledge base via the Foundry SDK
- [Advanced Lab 08: Multi-Agent Solution with Agent Framework]({{ '/adv-lab-08-multi-agent-framework.html' | relative_url }}) — automate the pipeline from Lab 04 with code

{% include lab-navigation.html %}
