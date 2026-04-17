---
layout: page
title: Prerequisites
---

Use this checklist at least 3 days before delivery.

## Participant Prerequisites

1. Active Azure subscription with permission to create and edit resources.
2. Microsoft Foundry project access.
3. Azure AI Search access.
4. Azure Logic Apps access.
5. Contributor access in the target subscription or resource group.
6. Browser access to Azure portal.
7. GitHub account.

## Facilitator Prerequisites

1. Validate all labs end to end in a clean subscription.
2. Prepare a backup demo environment in case participant provisioning fails.
3. Ensure no tenant policy blocks connector connection creation.
4. Pre-stage sample prompts and test payloads.
5. Have a fallback tool path using built-in HTTP if managed connectors are blocked.

## Azure Resource Checklist

- Resource Group created.
- Foundry project created and accessible.
- Model endpoint and deployment name confirmed.
- Logic Apps workflow app deployed and healthy.
- Storage account linked to Logic Apps Standard.
- Azure AI Search service deployed and accessible.
- Connection references for connectors and tools planned.

## Cost and Quota Notes

- Agent runs consume model tokens.
- Connector usage can incur costs depending on plan and connector tier.
- Validate regional model availability before workshop day.

## Pre-Workshop Validation Steps

1. Open Azure portal.
2. Go to your Logic Apps Standard resource.
3. Verify Workflows blade loads successfully.
4. Verify you can create an Autonomous Agents workflow kind.
5. Verify model connection can be created from agent loop.
6. Run a simple test call and confirm run history appears.

## Optional Local Tools

These are required for this workshop runbook.

- Python 3.10+
- VS Code
- PowerShell 7+ or curl

## Sample Test Request Payload

Use this payload when invoking the HTTP trigger:

```json
{
  "userRequest": "Summarize severe weather alerts in Washington and send email updates",
  "outputMode": "email"
}
```
