---
layout: page
title: "Lab 05: End-to-End Scale-Out and Demos"
nav_order: 5
lab_id: lab-05
category: beginner
---

{% include lab-navigation.html %}

## Lab Summary

In this lab you will validate the complete flow, discuss scale-out architecture, and run participant demos.

## Estimated Time

- 45 minutes

## Learning Objectives

1. Validate end-to-end Foundry + Logic Apps behavior.
2. Identify scale-out and reliability considerations.
3. Present architecture and operational readiness.

## Step 1: End-to-end validation run

1. Trigger the full workflow using a realistic enterprise prompt.
2. Confirm Foundry agent reasoning path.
3. Confirm Logic App enterprise action execution.
4. Confirm final user-facing response quality.

Checkpoint:

- Full scenario completes without manual intervention.

## Step 2: Reliability stress checks

1. Run 5 repeated requests with slight variations.
2. Observe latency and failure behavior.
3. Validate retries and graceful failure responses.

Checkpoint:

- Team identifies reliability bottlenecks and mitigation actions.

## Step 3: Scale-out discussion points

Review the following design topics:

1. Concurrency limits and throughput handling.
2. Token and model cost monitoring.
3. Connector throttling and backoff strategy.
4. Separation of read-only and write tools.
5. Observability and run diagnostics strategy.
6. Environment promotion strategy (dev/test/prod).

Checkpoint:

- A production-readiness action list is documented.

## Step 4: Participant demos

Each participant or team presents:

1. Architecture and scenario.
2. Prompt and tool design.
3. One issue found and how it was fixed.
4. Evaluation findings and next improvements.

## Step 5: Closing checklist

1. Save and export notes.
2. Capture unresolved blockers.
3. Assign owners for productionization tasks.

## Lab Completion Criteria

- End-to-end flow validated.
- Scale-out risks identified.
- Demo walkthrough completed.

{% include lab-navigation.html %}
