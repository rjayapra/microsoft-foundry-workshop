---
layout: page
title: "Lab 03: Build Logic App Consumption Workflow and External Tools"
nav_order: 3
lab_id: lab-03
---

{% include lab-navigation.html %}

## Lab Summary

In this lab you will build a Logic App consumption workflow with a trigger and enterprise action, expose connector actions as tools, and validate integration with your Foundry agent.

## Estimated Time

- 75 minutes

## Learning Objectives

1. Build a consumption workflow in Logic Apps.
2. Connect workflow actions to the agent tool pattern.
3. Add a connector-backed read-only tool.
4. Add an optional authenticated connector tool.
5. Apply safe and reliable connector practices.

## Prerequisite

- Complete Lab 01 and Lab 02.

## Part 1: Create consumption workflow with trigger

### Step 1: Create workflow shell

1. Open your Logic Apps Standard resource.
2. Select Workflows and create a new workflow.
3. Name it AgentConsumptionFlow.
4. Add trigger: When a HTTP request is received.
5. Save once to generate trigger URL.

Checkpoint:

- Workflow has a valid HTTP trigger endpoint.

### Step 2: Add enterprise action

1. Add one enterprise action aligned to customer scenario, for example:
- Outlook send email
- ServiceNow query
- Internal REST API call (HTTP action)
2. Configure action with deterministic test values.
3. Save workflow.

Checkpoint:

- Workflow runs trigger plus enterprise action successfully.

## Part 2: Add read-only connector tool (MSN Weather)

### Step 1: Add connector action as tool

1. Open your agent orchestration workflow.
2. Inside the agent tool area, select Add an action.
3. Search for connector: MSN Weather.
4. Select action: Get current weather.
5. Set tool metadata:
- Name: Get current Seattle weather
- Description: Gets current weather conditions in Seattle.

Checkpoint:

- Connector-backed tool appears in the tool list.

### Step 2: Configure connector action inputs

1. Open action settings.
2. Set Location: Seattle, US.
3. Set Units: Imperial.
4. Save workflow.

Checkpoint:

- Action validates and saves without errors.

### Step 3: Validate tool usage in run history

1. Trigger workflow using test prompt requiring weather lookup.
2. Open Run history.
3. Confirm tool was invoked.
4. Validate connector action output payload.

Checkpoint:

- Agent successfully calls weather connector tool.

## Part 3 (Optional): Add authenticated GitHub tool

### Step 1: Add GitHub connector action

1. Add a new action in the same tool area.
2. Search GitHub connector.
3. Select read-only action such as list repositories for authenticated user.

### Step 2: Create or select GitHub connection

1. Select GitHub action.
2. In connection pane, sign in to GitHub.
3. Grant required scopes.
4. Confirm connection state is connected.

Checkpoint:

- GitHub connector is authorized.

### Step 3: Configure tool metadata and test

1. Set tool name: Get GitHub repositories.
2. Set description: Gets my public and private GitHub repositories.
3. Save workflow.
4. Trigger workflow with repository summary prompt.
5. Validate tool invocation in run history.

Checkpoint:

- Authenticated tool executes successfully.

## Best Practices Applied in this Lab

1. Prefer read-only tools during initial rollout.
2. Use least-privilege connector permissions.
3. Write precise tool descriptions to improve tool selection.
4. Validate and constrain tool inputs.
5. Handle 401, 403, 404, 429, and timeout patterns gracefully.
6. Use run history for iterative tuning.

## Lab Completion Criteria

- Consumption workflow exists and runs.
- At least one connector action is exposed as tool.
- Participant validates tool call in run history.
- Participant explains connector authentication and least-privilege strategy.

{% include lab-navigation.html %}
