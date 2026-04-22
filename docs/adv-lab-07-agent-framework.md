---
layout: page
title: "Advanced Lab 07: Microsoft Agent Framework SDK"
nav_order: 16
lab_id: adv-lab-07
category: advanced
---

{% include lab-navigation.html %}

## Lab Summary

Use the **Microsoft Agent Framework SDK** to create an AI agent entirely in code. Instead of configuring agents in the portal, you define the agent, its tools, and the runtime execution loop programmatically — giving you full control over agent behaviour, tool registration, and conversation management.

## Estimated Time

30 minutes

## Learning Objectives

1. Understand the Microsoft Agent Framework SDK architecture.
2. Create an Azure AI Agent using the SDK from Python.
3. Register a custom function (tool) and handle tool calls in the execution loop.
4. Run multi-turn conversations and process streamed responses.

## Prerequisites

- An Azure subscription with a deployed Foundry project and model.
- Visual Studio Code installed.
- Python 3.12 or later installed.

---

## Scenario

You'll build an **Expense Claims Agent** that processes employee expense submissions. The agent uses a custom function tool to validate and save expense data — demonstrating the full SDK-based agent development workflow.

---

## Step 1: Set up the project

1. Clone the repository and navigate to `Labfiles/07-agent-framework/Python`.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Create a `.env` file with your project connection string:
   ```
   PROJECT_CONNECTION_STRING=<your-connection-string>
   MODEL_DEPLOYMENT_NAME=gpt-4o
   ```

## Step 2: Review the SDK architecture

Open `agent_framework.py` and examine the key components:

| Component | Purpose |
|-----------|---------|
| `AIProjectClient` | Connection to your Foundry project |
| `agents.create_agent()` | Defines the agent with a name, instructions, and tools |
| `FunctionTool` | Registers a Python function as an agent-callable tool |
| `agents.create_thread()` | Creates an isolated conversation thread |
| `agents.create_run()` | Starts agent reasoning over a thread |
| `EventHandler` | Handles streaming events (messages, tool calls, errors) |

## Step 3: Define the custom tool function

Locate the expense processing function and review its signature:

```python
def process_expense_claim(
    employee_id: str,
    description: str,
    amount: float,
    category: str
) -> str:
    """
    Validates and records an expense claim.
    Returns a confirmation message with a claim reference ID.
    """
    ...
```

The function is registered using `FunctionTool` so the agent can invoke it autonomously.

## Step 4: Create and run the agent

1. Review how the agent is created with instructions:
   ```python
   agent = project_client.agents.create_agent(
       model=model_deployment_name,
       name="expense-claims-agent",
       instructions="""
           You are an expense claims specialist. Help employees submit expense claims
           by collecting: employee ID, expense description, amount, and category
           (travel, meals, equipment, or other). Use the process_expense_claim tool
           to submit each claim. Confirm submission with the provided reference ID.
       """,
       tools=functions.definitions
   )
   ```
2. Run the agent:
   ```bash
   python agent_framework.py
   ```
3. At the prompt, try:
   - *"I need to submit an expense for a team lunch costing $87.50."*
   - *"My employee ID is EMP-4421. Please categorise it as meals."*
4. Verify the agent autonomously calls `process_expense_claim` and returns a reference ID.

## Step 5: Implement the tool call handling loop

Review the execution loop that handles tool invocations during a run:

```python
while run.status in ["queued", "in_progress", "requires_action"]:
    if run.status == "requires_action":
        # Process tool calls from the agent
        tool_outputs = []
        for tool_call in run.required_action.submit_tool_outputs.tool_calls:
            output = functions.execute(tool_call)
            tool_outputs.append({"tool_call_id": tool_call.id, "output": output})
        run = project_client.agents.submit_tool_outputs_to_run(thread_id, run.id, tool_outputs)
    run = project_client.agents.get_run(thread_id, run.id)
```

This pattern ensures the agent's tool calls are always fulfilled before it continues reasoning.

---

## Clean up

Delete the agent using `project_client.agents.delete_agent(agent.id)`, and delete the Azure resource group when finished with all Advanced Labs.

## Summary

In this lab you:
- Created an agent entirely in Python using the Microsoft Agent Framework SDK.
- Registered a custom function as an agent-callable tool.
- Implemented the tool-call handling loop for multi-turn, tool-augmented conversations.

**Next:** [Advanced Lab 08: Multi-Agent Solution]({{ '/adv-lab-08-multi-agent-framework.html' | relative_url }})
