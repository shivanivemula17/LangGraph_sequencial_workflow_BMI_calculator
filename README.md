# BMI Calculator with Category Classification – LangGraph

## Overview

This project demonstrates the implementation of a **Sequential Workflow using LangGraph** by building a BMI (Body Mass Index) Calculator with automatic category classification.

The workflow takes a person's weight and height as input, calculates their BMI, and determines the corresponding BMI category through a sequence of interconnected nodes.

This is a basic, non-LLM workflow designed to understand the fundamental concepts of LangGraph, including State, Nodes, Edges, Graph Compilation, and Workflow Execution.

## Objective

To understand how LangGraph orchestrates multiple processing steps in a predefined sequence, where the output of one node becomes available to the next node through a shared state.

## Workflow Architecture

The workflow consists of two processing nodes:

```text
          START
            |
            v
     Calculate BMI
            |
            v
       Label BMI
            |
            v
           END
```

### 1. Calculate BMI Node

- Accepts weight (in kilograms) and height (in meters).
- Calculates BMI using the standard formula.
- Rounds the calculated BMI to two decimal places.
- Updates the shared workflow state with the calculated BMI.

**Formula:**

BMI = Weight (kg) / Height (m)²

### 2. Label BMI Node

- Receives the calculated BMI from the previous node.
- Evaluates the BMI against predefined classification ranges.
- Assigns the corresponding BMI category.
- Updates the workflow state with the category.

**BMI Classification:**

| BMI Range | Category |
|---|---|
| Below 18.5 | Underweight |
| 18.5 – 24.9 | Normal |
| 25.0 – 29.9 | Overweight |
| 30.0 and above | Obese |

*Note: These are standard adult BMI screening categories, not a medical diagnosis.*

## LangGraph Concepts Implemented

| Concept | Description |
|---|---|
| TypedDict | Defines the structure and data types of the workflow state. |
| StateGraph | Creates the graph using the defined state schema. |
| State | Maintains weight, height, calculated BMI, and category. |
| Nodes | Represents individual processing functions. |
| Edges | Defines the execution sequence between nodes. |
| START | Represents the entry point of the workflow. |
| END | Represents the termination point of the workflow. |
| Compile | Converts the graph definition into an executable workflow. |
| Invoke | Executes the workflow using the initial input state. |
| Graph Visualization | Generates a visual representation of the workflow using Mermaid. |

## Technologies & Libraries

- **Python** – Core programming language.
- **LangGraph** – Workflow orchestration and graph execution.
- **IPython** – Displays the generated workflow graph inside Jupyter Notebook.
- **Jupyter Notebook** – Development and execution environment.
- **TypedDict** – Defines the workflow state structure.

## Installation

Install the required libraries:

```bash
pip install langgraph ipython
```

## Workflow Execution

The workflow follows these steps:

1. Define the BMI state using `TypedDict`.
2. Create the `calculate_bmi` node.
3. Create the `label_bmi` node.
4. Initialize the graph using `StateGraph`.
5. Register both processing nodes.
6. Connect the nodes using edges.
7. Compile the graph using `graph.compile()`.
8. Execute the workflow using `workflow.invoke()`.
9. Visualize the workflow using Mermaid.

## Expected Output

**Sample Input:**

```python
{
    "weight": 70,
    "height": 1.75
}
```

**Expected Result:**

```python
{
    "weight": 70,
    "height": 1.75,
    "bmi": 22.86,
    "category": "Normal"
}
```

## Key Learnings

Through this project, I learned:

- How to create a basic LangGraph workflow.
- How to define and manage shared state using `TypedDict`.
- How to create independent processing nodes using Python functions.
- How to connect nodes using directed edges.
- How data flows between sequential nodes.
- How to compile and execute a LangGraph workflow.
- How to visualize the workflow architecture.

---

**Project Type:** Sequential Workflow  
**Framework:** LangGraph  
**Category:** Agentic AI / Workflow Orchestration  
**LLM Integration:** Not Used
