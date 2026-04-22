---
layout: page
title: "Lab 04: Foundry Evaluation and Automation"
nav_order: 4
lab_id: lab-04
category: beginner
---

{% include lab-navigation.html %}

## Lab Summary

In this lab you will define evaluation goals, prepare a dataset, configure evaluators, run evaluations, and automate repeated runs.

## Estimated Time

- 70 minutes

## Learning Objectives

1. Define measurable evaluation objectives.
2. Build a test dataset aligned to expected behavior.
3. Configure built-in and custom evaluators.
4. Run and compare evaluation results.
5. Automate evaluation execution for iterative improvement.

## Step 1: Define evaluation objectives

1. Identify quality goals for your agent, for example:
- Relevance
- Groundedness
- Safety
- Task completion
2. Define target thresholds for each metric.

Checkpoint:

- You have a metric checklist and baseline targets.

## Step 2: Prepare evaluation dataset

1. Create a JSONL dataset with prompts and expected qualities.
2. Include at least 20 records with mixed scenarios:
- Normal cases
- Ambiguous requests
- Failure-prone requests
3. Store dataset in your workshop folder or Foundry dataset asset.

Example JSONL entry:

```json
{"input":"Summarize severe weather alerts for Washington.","context":"Weather scenario","expected":"Concise severe alert summary"}
```

Checkpoint:

- Dataset is uploaded and available for evaluation run.

## Step 3: Configure evaluators

1. In Foundry evaluation experience, create a new evaluation run.
2. Select your target agent/workflow.
3. Select dataset from Step 2.
4. Add evaluators based on goals:
- Response quality evaluator
- Groundedness evaluator
- Safety evaluator
- Optional custom evaluator

Checkpoint:

- Evaluation configuration is complete and saved.

## Step 4: Execute and review results

1. Run evaluation.
2. Wait for completion.
3. Review aggregate scores.
4. Drill into low-performing rows.
5. Capture top 3 failure patterns.

Checkpoint:

- You can explain strongest and weakest metrics.

## Step 5: Improve and rerun

1. Apply one instruction improvement in agent prompt.
2. Apply one tool description improvement.
3. Re-run evaluation using the same dataset.
4. Compare trends between run 1 and run 2.

Checkpoint:

- At least one metric improves after iteration.

## Step 6: Automate evaluation runs

1. Choose automation trigger:
- Manual schedule
- CI pipeline trigger
- Post-change validation
2. Define minimal automation flow:
- Load dataset
- Run evaluation
- Export report
- Notify team on regression

Checkpoint:

- Team has a repeatable evaluation loop.

## Lab Completion Criteria

- Evaluation objectives are documented.
- At least two evaluation runs are compared.
- Automation approach is documented for customer team.

{% include lab-navigation.html %}
