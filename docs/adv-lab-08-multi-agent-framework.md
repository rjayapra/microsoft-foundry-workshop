---
layout: page
title: "Advanced Lab 08: Multi-Agent Solution with Agent Framework"
nav_order: 17
lab_id: adv-lab-08
category: advanced
---

{% include lab-navigation.html %}

## Lab Summary

Implement a **sequential multi-agent orchestration pattern** using the Microsoft Agent Framework SDK. You'll build a pipeline of three specialised agents that collaboratively process customer feedback — each agent hands its output to the next, forming an automated reasoning chain.

## Estimated Time

30 minutes

## Learning Objectives

1. Understand the sequential orchestration pattern in a multi-agent pipeline.
2. Create multiple specialised agents with distinct roles using the Agent Framework SDK.
3. Pass structured output between agents as context for downstream reasoning.
4. Run an end-to-end pipeline from raw feedback to recommended action.

## Prerequisites

- An Azure subscription with a deployed Foundry project and model.
- Visual Studio Code installed.
- Python 3.12 or later installed.
- Completion of [Advanced Lab 07]({{ '/adv-lab-07-agent-framework.html' | relative_url }}) is recommended (same SDK patterns).

---

## Scenario

You'll process customer product feedback through a **three-stage pipeline**:

1. **Summariser Agent** — condenses raw, verbose feedback into a single neutral sentence.
2. **Classifier Agent** — categorises the summarised feedback as *Positive*, *Negative*, or *Feature Request*.
3. **Recommended Action Agent** — suggests the most appropriate follow-up step based on category and summary.

---

## Step 1: Set up the project

1. Clone the workshop repository (if you haven't already):
   ```bash
   git clone https://github.com/rjayapra/microsoft-foundry-workshop.git
   cd microsoft-foundry-workshop
   ```
   Then navigate to `Labfiles/adv-lab-08-multi-agent-framework/Python`.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Create a `.env` file:
   ```
   PROJECT_ENDPOINT=<your-project-endpoint>
   MODEL_DEPLOYMENT_NAME=gpt-5.1
   ```

## Step 2: Understand the pipeline structure

Open `agents.py` and review how each agent is defined:

```python
summariser = project_client.agents.create_agent(
    model=MODEL,
    name="summariser-agent",
    instructions="""
        Condense the following customer feedback into exactly one neutral sentence.
        Do not add opinions or analysis — just summarise what was said.
    """
)

classifier = project_client.agents.create_agent(
    model=MODEL,
    name="classifier-agent",
    instructions="""
        Classify the following feedback summary as one of: Positive, Negative, or Feature Request.
        Respond with only the category label.
    """
)

action_recommender = project_client.agents.create_agent(
    model=MODEL,
    name="action-recommender-agent",
    instructions="""
        Given a customer feedback summary and its category, suggest the single most appropriate
        follow-up action for the support team. Be specific and actionable.
    """
)
```

## Step 3: Implement the sequential pipeline

The pipeline runs three sequential agent calls, feeding each output as the next agent's input:

```python
def run_agent(agent_id, prompt):
    thread = project_client.agents.create_thread()
    project_client.agents.create_message(thread.id, role="user", content=prompt)
    run = project_client.agents.create_and_process_run(thread.id, agent_id=agent_id)
    messages = project_client.agents.list_messages(thread.id)
    return messages.get_last_message_by_role("assistant").content[0].text.value

# Stage 1: Summarise
summary = run_agent(summariser.id, raw_feedback)

# Stage 2: Classify the summary
category = run_agent(classifier.id, summary)

# Stage 3: Recommend action based on both
action = run_agent(action_recommender.id, f"Summary: {summary}\nCategory: {category}")
```

## Step 4: Run the pipeline

1. Run the script:
   ```bash
   python agents.py
   ```
2. The script runs the pipeline against three sample feedback entries. Verify output similar to:

   ```
   === Feedback 1 ===
   Raw:       "I've been waiting 3 weeks for my order and no one responds to ..."
   Summary:   Customer reports unresolved delayed order with no support response.
   Category:  Negative
   Action:    Escalate the case to a senior support agent and prioritise a refund or reship.

   === Feedback 2 ===
   Raw:       "Love the product! Would be amazing if it had a dark mode ..."
   Summary:   Customer is satisfied and requesting a dark mode feature.
   Category:  Feature Request
   Action:    Log the dark mode request in the product backlog with +1 vote.
   ```

## Step 5: Extend the pipeline (optional)

Try extending the pipeline with a fourth agent:

**Sentiment Score Agent** — rates the feedback sentiment from 1 to 10 and justifies the score.

Add it after the Classifier and feed both summary and category as input.

---

## Clean up

Delete each agent after the run with `project_client.agents.delete_agent(agent.id)`, and delete the Azure resource group when finished with all Advanced Labs.

## Summary

In this lab you:
- Implemented a three-stage sequential orchestration pattern using the Microsoft Agent Framework SDK.
- Passed structured outputs between specialised agents to form an automated reasoning pipeline.
- Processed customer feedback end-to-end from raw text to recommended action.

---

> You have completed all **Advanced Labs**. Return to the [workshop home]({{ '/' | relative_url }}) for the full lab list, or visit the [Post-Workshop]({{ '/post-workshop.html' | relative_url }}) page for next steps and additional learning resources.
