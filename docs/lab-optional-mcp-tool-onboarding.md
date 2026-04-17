# Optional Lab: MCP Tool Onboarding to Foundry

## Lab Summary

This optional lab shows how to define and onboard an MCP tool so the Foundry agent can call it with clear schema and safe usage boundaries.

## Estimated Time

- 35 minutes

## Learning Objectives

1. Create an MCP tool endpoint contract.
2. Define tool schema and descriptions for effective tool selection.
3. Onboard MCP tool into Foundry agent.
4. Validate calls and troubleshoot common onboarding issues.

## Step 1: Define MCP tool contract

1. Choose one safe read-only capability, for example:
- Internal status lookup
- Catalog search
- Policy reference retrieval
2. Define tool input schema.
3. Define output schema.

Checkpoint:

- Tool contract is documented and reviewable.

## Step 2: Implement MCP tool endpoint

1. Create MCP server/tool implementation in your preferred runtime.
2. Add input validation.
3. Return consistent JSON structure.
4. Add clear error responses.

Checkpoint:

- Tool endpoint responds correctly to test inputs.

## Step 3: Register MCP tool in Foundry

1. Open Foundry agent configuration.
2. Add MCP tool connection.
3. Provide tool name, description, and schema.
4. Save agent configuration.

Checkpoint:

- Foundry agent shows MCP tool as available.

## Step 4: Validate tool invocation

1. Send prompt that should trigger MCP tool usage.
2. Inspect agent trace for tool selection.
3. Verify tool arguments match expected schema.
4. Confirm response quality after tool call.

Checkpoint:

- Agent invokes MCP tool successfully.

## Step 5: Apply best practices

1. Keep tool names action-oriented.
2. Use precise descriptions including when not to use the tool.
3. Enforce input constraints.
4. Prefer read-only access for initial rollout.

## Lab Completion Criteria

- MCP tool is callable by agent.
- Schema and descriptions are validated.
- Team can explain secure rollout path.
