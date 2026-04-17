---
layout: page
title: Lab 01
---

## Lab Summary

In this lab you will create an agent in Microsoft Foundry, define instruction patterns for reliable tool usage, configure model parameters, and validate reasoning quality.

## Estimated Time

- 130 minutes (09:35 to 11:45 slot)

## Learning Objectives

1. Create a new agent in Foundry.
2. Define high-quality instructions that drive safe tool use.
3. Configure model deployment and runtime settings.
4. Validate reasoning behavior with structured tests.

## Step 1: Create a new Foundry agent

1. Open https://ai.azure.com and enter your Foundry project.
2. Go to Agents and select Create new agent.
3. Provide name: SevereWeatherAgent.
4. Provide purpose: Summarize severe weather alerts and trigger notification actions.
5. Save agent.

Checkpoint:

- Agent is visible in your project assets.

## Step 2: Configure model and parameters

1. Open agent configuration.
2. Select chat-capable model deployment.
3. Set initial runtime parameters:
- Temperature: 0.2
- Max output tokens: 800
- Top P: 1.0
4. Save configuration.

Checkpoint:

- Agent is connected to a healthy model deployment.

## Step 3: Author instructions for tool usage

1. Open Instructions field in the agent.
2. Add structured instructions:

```text
You are an enterprise weather operations assistant.

Goals:
1) Retrieve severe weather alerts.
2) Summarize only actionable items.
3) Avoid duplicate and non-severe content.
4) Produce concise output with clear next actions.

Tool behavior:
- Use weather retrieval tools first when current conditions are requested.
- Use notification tools only after summary is prepared.
- If tool output is missing or invalid, return a short fallback response.

Safety:
- Do not invent tool results.
- Keep responses factual and concise.
```

3. Save instructions.

Checkpoint:

- Instructions include clear goals, tool behavior, and safety boundaries.

## Step 4: Add first tool definition

1. Add a weather data retrieval tool in agent tools.
2. Set tool name: Get weather alert data.
3. Set description: Retrieves active severe weather alerts by state.
4. Define expected input schema:
- stateCode (string, required)
5. Define expected output schema:
- alerts (array)
- summary (string)
6. Save tool.

Checkpoint:

- Tool metadata is explicit and schema is valid.

## Step 5: Add notification tool definition

1. Add second tool in the agent.
2. Set tool name: Send email to subscriber.
3. Set description: Sends formatted weather summary to configured recipients.
4. Define input schema:
- subject (string)
- bodyHtml (string)
- recipient (string)
5. Save tool.

Checkpoint:

- Agent has two tools with non-overlapping responsibilities.

## Step 6: Test agent reasoning

Run the following prompts in agent test panel:

1. "Summarize severe alerts for Washington and notify subscribers."
2. "Check weather in Washington and include only high-impact events."
3. "Provide brief update if there are no severe alerts."

For each test, verify:

1. Tool calls are logical and ordered.
2. Output is concise and actionable.
3. No fabricated data is present.

Checkpoint:

- Agent produces stable and high-quality behavior across test prompts.

## Step 7: Tune parameters and retest

1. Increase Temperature to 0.5 and rerun one test.
2. Compare consistency and quality.
3. Set Temperature back to recommended value for deterministic behavior.

Checkpoint:

- Team understands parameter tradeoffs between creativity and consistency.

## Lab Completion Criteria

- Foundry agent created and configured.
- Instructions drive predictable tool usage.
- Model and parameter settings are validated.
- Test prompts show reliable reasoning.
