<p align="right">
  <a href="./README.ko.md">🇰🇷 Korean</a> | 🇺🇸 English
</p>

# Agent Pattern Practice Lab

This repository explores the evolution of LLM-based Agent Architectures
through hands-on experiments \
from ReAct-centered first-generation agents to workflow-orchestrated
Post-ReAct systems.

------------------------------------------------------------------------

# Common Setup

Initializes the shared environment and tools used throughout all
experiments.

## 0. TEST

-   Verifies LLM connectivity and API key configuration
-   Establishes a working baseline before running agent experiments

## 1. Tools

-   Defines external tools such as Tavily Search
-   Connects tools via the LangChain Tool interface
-   Prepares the Action Layer used by agents

------------------------------------------------------------------------

# \[Gen 1\] Prompt-driven Tool-Using Agents (ReAct-based Agents)

Experiments with first-generation agent patterns where the LLM
independently performs the Reason → Act → Observe loop.

## 1. Zero-Shot ReAct

-   The purest form of the ReAct pattern
-   No planning phase; reasoning happens on-the-fly
-   The LLM owns the entire workflow decision process

## 2. Conversational ReAct

-   ReAct augmented with conversation history (memory)
-   Observes behavioral changes when context is accumulated
-   Transition from stateless to context-aware reasoning

## 3. Search-augmented ReAct (Self-Ask with Search)

-   Breaks problems into sub-questions (Self-Ask strategy)
-   Integrates external search tools for information retrieval tasks

## 4. ReAct Docstore

-   Performs QA against a provided document store
-   Demonstrates that even with retrieval, control still resides in the
    LLM

------------------------------------------------------------------------

# \[Gen 2\] LLM Orchestrated Systems (Post-ReAct Agents)

Moves beyond LLM-driven control toward system-designed execution, where
the workflow is defined externally and the LLM acts as a component.

## 1. Plan-Then-Execute (Two-Phase Execution Architecture)

-   Separates planning and execution into distinct phases
-   Introduces structural determinism absent in ReAct

## 2. State Machine (FSM-based Orchestration)

-   Defines explicit states and transitions
-   Treats the agent as part of a controlled workflow rather than a
    free-form conversation

## 3. Graph Execution (DAG Workflow Engine)

-   Introduces DAG-based execution modeling
-   Enables non-linear workflows and reusable nodes

## 4. DAG-Orchestrated Stateful Execution (FSM + Graph)

-   Combines FSM state control with DAG execution
-   Approximates real-world orchestration architectures

## 5. Role-Specialized Multi-Agent System

-   Splits responsibilities across Planner / Researcher / Builder /
    Critic / Supervisor roles
-   Implements a collaborative multi-agent system

## 6. Deterministic Guardrail

-   Adds validation and guardrail mechanisms
-   Ensures outputs are controlled at the system level rather than
    blindly trusting LLM responses

------------------------------------------------------------------------

## Summary

Gen1: LLM-driven systems where the model decides *what to do and when to
do it*.

Gen2: System-driven orchestration where the workflow is engineered and
the LLM plays a bounded role.

This lab demonstrates that building LLM agents is no longer just prompt
engineering ---\
it is fundamentally a **software architecture problem**.
