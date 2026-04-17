# Troubleshooting Guide

Use this guide during workshop delivery to quickly unblock participants.

## Failure: Cannot create model connection in agent loop

Symptoms:

- Connection creation fails.
- Model deployment not visible.

Checks:

1. Confirm correct subscription and region.
2. Confirm deployed model exists and is active.
3. Confirm participant has permission to access model resource.

Fix:

1. Re-open agent loop and reselect resource.
2. Recreate connection.
3. Switch to facilitator backup model deployment if needed.

## Failure: Agent does not call tool

Symptoms:

- Agent responds directly without tool use.

Checks:

1. Tool name is clear and action-oriented.
2. Tool description states when the tool should be used.
3. Prompt explicitly instructs tool usage.

Fix:

1. Rewrite tool description to be specific.
2. Reduce overlap with other tool descriptions.
3. Add explicit instruction: call tool before final response.

## Failure: HTTP action errors

Common status patterns:

1. 401 or 403: authentication/authorization problem.
2. 404: bad endpoint or parameters.
3. 429: throttling.
4. 500+: upstream service instability.

Fix:

1. Validate endpoint URL and query parameters.
2. Add retry policy where suitable.
3. Add guardrail text in prompt for transient failures.

## Failure: Connector shows Not authorized

Checks:

1. Connection is using expected identity.
2. OAuth consent was completed.
3. Required scopes are granted.

Fix:

1. Reauthenticate connector.
2. Regenerate or rotate token if needed.
3. Validate account has access to target resources.

## Failure: Trigger URL returns 401/404

Checks:

1. Workflow is saved and enabled.
2. URL copied from current trigger.
3. HTTP method is POST.
4. Content-Type is application/json.

Fix:

1. Re-save workflow to refresh trigger endpoint.
2. Use minimal payload and retry.

## Failure: Email tool succeeds but no email received

Checks:

1. Recipient address is valid.
2. Junk folder and safe sender policies.
3. Connector account mailbox send permissions.

Fix:

1. Send to facilitator mailbox for control test.
2. Add a fixed test subject marker for filtering.

## Diagnostic Process (fast triage)

1. Check run status.
2. Open failed action.
3. Read inputs and outputs.
4. Classify issue: model, tool mapping, connector auth, runtime.
5. Apply targeted fix and rerun.
