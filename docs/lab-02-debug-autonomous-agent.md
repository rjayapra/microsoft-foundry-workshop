---
layout: page
title: "Lab 02: Debug Agent Reasoning and Tool Execution"
nav_order: 2
lab_id: lab-02
category: beginner
---

{% include lab-navigation.html %}

## Lab Summary

In this lab you will inspect Foundry traces and Logic Apps run history, trace reasoning steps, inspect tool arguments, and identify root causes quickly.

## Estimated Time

- 40 minutes

## Learning Objectives

1. Inspect Foundry test traces for reasoning quality.
2. Inspect Logic Apps run history for workflow and connector issues.
3. Analyze action-level inputs and outputs.
4. Distinguish model, tool-schema, and integration failures.

## Prerequisite

- Complete Lab 01.

## Step 1: Open Foundry trace view

1. In Foundry, open your agent test history.
2. Select a recent test run.
3. Review reasoning path and tool selection order.

Checkpoint:

- You can see agent steps, tool requests, and final response.

## Step 2: Open Logic Apps run history

1. Open Azure portal.
2. Open Logic Apps Standard workflow used by your agent orchestration.
3. Open Run history and select latest run.
4. Locate trigger, agent-connected action, and downstream tool actions.

Checkpoint:

- You can correlate Foundry trace steps with Logic Apps action execution.

## Step 3: Inspect model input and output details

1. In Foundry trace, inspect model input context.
2. Verify system instructions are present and correct.
3. Inspect tool call request payload.
4. Inspect model output quality and safety.
5. Review token usage and latency if available.

Checkpoint:

- You can identify what context was sent to the model and how it responded.

## Step 4: Inspect tool action details

1. In Logic Apps run, open weather retrieval action.
2. Validate input parameters.
3. Validate status code and output payload.
4. Open notification action.
5. Validate mapped subject and body values.

Checkpoint:

- You can verify each tool call had correct parameters and outputs.

## Step 5: Run controlled debugging experiments

### Experiment A: Ambiguous request

1. Run prompt with unclear objective.
2. Observe whether agent over-assumes user intent.
3. Tighten instruction policy and rerun.

### Experiment B: Tool naming quality

1. Temporarily rename tool to vague name.
2. Rerun prompt and inspect selection quality.
3. Restore descriptive tool name.

### Experiment C: Connector failure simulation

1. Provide invalid input for one connector action.
2. Inspect error propagation behavior.
3. Add fallback instruction and verify response quality.

Checkpoint:

- You can demonstrate that prompt quality and tool descriptions change runtime behavior.

## Step 6: Root cause classification

For any failed run, classify root cause using this matrix:

1. Model misalignment:
- Incorrect reasoning despite valid tool outputs.
- Fix by improving instructions and examples.

2. Tool schema or mapping issue:
- Wrong parameters sent to tool.
- Fix by correcting tool input mapping.

3. Connector or API issue:
- 401/403/404/429/500 response from action.
- Fix connection, permissions, or retry behavior.

4. Workflow runtime issue:
- Trigger or action dependency failure.
- Fix control flow and retry settings.

Checkpoint:

- Participant can identify issue category and propose remediation.

## Lab Completion Criteria

- Participant can inspect Foundry and Logic Apps diagnostics.
- Participant can explain token, reasoning, and execution traces.
- Participant can classify at least one issue and provide a fix path.

{% include lab-navigation.html %}
