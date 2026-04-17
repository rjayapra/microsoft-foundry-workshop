---
layout: page
title: Facilitator guide
---

## How to Use This Guide

This guide helps you run the workshop smoothly with clear pacing, checkpoints, and fallback options.

## Delivery Strategy

1. Demo first, then let participants execute.
2. Keep a checkpoint every 15 to 20 minutes.
3. Encourage pairs so one person configures while the other validates.
4. Use run history screenshots for students who fall behind.

## Time Management Tips

- Keep Foundry agent build as the anchor scenario.
- Treat MCP onboarding and GitHub connector as optional tracks.
- Reserve at least 30 minutes for troubleshooting and demos.

## Required Facilitator Assets

1. One ready-to-run reference Foundry project.
2. One backup model deployment in a second region if possible.
3. Prepared Logic Apps trigger test commands.
4. Known-good prompt and tool schema text for copy and paste.

## Live Demo Sequence

1. Show final working run first (2 minutes).
2. Show architecture of Foundry agent -> Logic Apps workflow -> enterprise action (5 minutes).
3. Walk through build steps with participants.
4. Show monitoring, traces, and token metadata for observability.

## Common Failure Modes and Fast Recovery

1. Model connection cannot be created.
- Recovery: verify resource, deployment, and access role; switch to backup deployment.

2. Agent does not call a tool.
- Recovery: tighten tool description and instruction language; reduce overlapping tools.

3. Connector authorization fails.
- Recovery: reauthenticate connection and validate required scopes.

4. HTTP trigger not reachable.
- Recovery: re-save workflow, regenerate trigger URL, test with minimal payload.

## Checkpoints

### Checkpoint 1 (end of Lab 01 build)

- Foundry agent exists.
- Model deployment and runtime parameters configured.
- Instructions and at least one tool schema are validated.

### Checkpoint 2 (end of Lab 02)

- Participant can inspect Foundry traces and Logic Apps run history.
- Participant can inspect tool arguments and outputs.
- Participant can identify whether issue is model-side, schema-side, or connector-side.

### Checkpoint 3 (end of Lab 03)

- Participant can build a consumption workflow and connector-backed tool.
- Participant can describe safe tool design and connector authentication principles.

## Suggested Challenge Prompts

1. Add a second weather tool for a different city and compare results.
2. Add a confirmation step before any write operation.
3. Refactor tool descriptions to improve tool selection.

## Debrief Questions

1. Where should business logic live: prompt, tool, or workflow action?
2. Which failures should be handled in tool action versus agent prompt?
3. How will you secure connector authentication in production?
