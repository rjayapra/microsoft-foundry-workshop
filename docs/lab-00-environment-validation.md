---
layout: page
title: "Lab 00: Environment Validation"
nav_order: 0
lab_id: lab-00
category: beginner
---

{% include lab-navigation.html %}

## Estimated Time

- 25 minutes

## Objective

Validate all prerequisites before hands-on implementation begins.

## Step 1: Validate Azure Access

1. Sign in to https://portal.azure.com.
2. Confirm target subscription is visible.
3. Confirm role assignment includes Contributor or equivalent for workshop resources.

Checkpoint:

- You can open subscription and resource groups without permission errors.

## Step 2: Validate Microsoft Foundry Access

1. Open https://ai.azure.com.
2. Open target Foundry project.
3. Confirm project resources load successfully.

Checkpoint:

- You can create or edit assets in the Foundry project.

## Step 3: Validate Model Deployment

1. In Foundry project, go to model deployments.
2. Confirm at least one chat-capable model deployment is in healthy state.
3. Record deployment name for later labs.

Checkpoint:

- Deployment name and endpoint are known.

## Step 4: Validate Azure AI Search Access

1. Open the Azure AI Search resource in portal.
2. Confirm service status is running.
3. Confirm you can view indexes.

Checkpoint:

- Search resource is reachable and usable.

## Step 5: Validate Logic Apps Access

1. Open Logic Apps Standard resource.
2. Open Workflows blade.
3. Confirm workflow designer loads.

Checkpoint:

- You can create and save workflows.

## Step 6: Validate Local Tooling

1. Open terminal and run:

```powershell
python --version
code --version
git --version
```

2. Confirm Python is 3.10 or newer.

Checkpoint:

- Local tools are available.

## Exit Criteria

- All platform and local checks pass.
- Participant is ready to begin Lab 01.

{% include lab-navigation.html %}
