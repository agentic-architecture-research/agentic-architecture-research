# The Evolution of Agentic Programming

## Purpose

This document introduces the core thesis behind **Agentic Architecture Research**.

The main claim:

> Agentic programming is not the end of traditional software engineering.
> It is the next abstraction layer inside software engineering.

Agentic systems still need the same engineering discipline as other software systems: constraints, validation, state management, observability, and failure recovery.

---

## Core Thesis

Current AI agent discourse often treats agents as a radical break from traditional software.

That framing is misleading.

Agentic programming is better understood as a new abstraction layer where software systems translate human intent into executable, verifiable workflows.

A useful mental model:

```txt
Intent → Execution Graph → Validation Loop
```

The abstraction is changing, but the foundations are not.

We are still building software.

---

## What Is Actually New?

The new challenge is not that software engineering disappears.

The new challenge is that we are integrating **non-deterministic components** into existing execution systems.

An LLM is not like a normal deterministic function.

The same input may produce different outputs, and those outputs may be incomplete, invalid, or expensive to retry.

So the engineering problem becomes:

```txt
How do we wrap fuzzy reasoning inside reliable software architecture?
```

---

## Optimizing for Distributed Systems Cost

In traditional software, optimization usually focuses on:

* execution speed
* infrastructure cost
* reliability
* usability

In agentic systems, the same concerns remain, but they expand.

Agentic cost includes:

| Cost Type         | Meaning                                                      |
| ----------------- | ------------------------------------------------------------ |
| Financial cost    | Tokens, compute, API calls, model usage                      |
| Latency           | Generation speed, execution time, network overhead           |
| Failure recovery  | Retries, validation failures, hallucination recovery, rework |
| Human supervision | Manual review, correction, approval, debugging               |

This is not fundamentally new.

It is distributed systems work with a new kind of compute node:

```txt
LLM = non-deterministic, expensive, high-latency compute node
```

Naive retry loops become expensive fast.

That is why structure matters.

---

## The Shift Toward Constraints

Reliable agentic systems cannot be built from vague prompts and unconstrained agent loops.

LLMs are non-deterministic. Left unconstrained, they create:

* unpredictable behavior
* escalating token cost
* unclear failure modes
* poor reproducibility
* difficult debugging
* fragile workflows

This forces agentic architecture toward constrained systems.

A common pattern looks like:

```txt
Input → Plan → Decompose → Execute → Validate → Loop
```

This resembles traditional workflow engines, job queues, and state machines.

That is not a weakness.

That is the point.

Agentic systems need proven software architecture around fuzzy components.

---

## Agents as Fuzzy Parsers

A production-ready agentic system should not give the LLM full execution authority.

The LLM should be used where it is strongest:

* interpreting intent
* generating candidate plans
* translating vague input into structured output
* reasoning over ambiguous information
* proposing actions

The deterministic control plane should own:

* routing
* execution
* state management
* validation
* retries
* logging
* permissions
* artifact storage
* failure handling

This reduces the LLM to something like a fuzzy parser inside a conventional state machine.

That is intentional.

```txt
LLM proposes.
Runtime constrains.
System validates.
```

---

## Why This Matters

The more serious agentic systems become, the more they need:

* atomic tasks
* scoped context
* hardcoded routing
* explicit contracts
* validation gates
* append-only logs
* replayable execution
* inspectable artifacts
* deterministic state transitions

These are not optional extras.

They are the engineering requirements for making non-deterministic systems usable.

---

## Existing Tooling Gap

Traditional workflow engines like Temporal or Prefect are built around deterministic services.

They are strong at orchestration, retries, and state management, but they do not naturally model:

* fuzzy routing
* dynamic task generation
* token-aware context scoping
* agent output validation
* non-deterministic planning

Agent frameworks often solve the opposite problem.

They make it easy to connect prompts, tools, and models, but often hide important execution details inside opaque chains.

Common weaknesses include:

* unclear state boundaries
* weak observability
* prompt-driven routing
* poor reproducibility
* hard-to-debug execution paths

The missing middle is:

```txt
Distributed-systems-grade control plane
+
LLM-aware execution boundaries
```

---

## Research Direction

Agentic Architecture Research explores this missing middle.

The research focuses on how structured execution layers can make agentic systems more:

* reliable
* cost-efficient
* inspectable
* reproducible
* debuggable
* composable

Current and future explorations include:

* structured task graphs vs. open-ended agent loops
* contract-driven development for agents
* plugin-based agentic workflows
* atomic task decomposition
* scoped context injection
* append-only execution logs
* deterministic control planes
* validation loops around agent outputs
* failure detection and recovery

---

## Practical Framing

Building reliable agentic workflows is not mostly frontier magic.

It is mostly software architecture.

More specifically:

```txt
Agentic systems are distributed systems with non-deterministic workers.
```

That means the field needs less mythology and more engineering discipline.

The goal is not to let agents improvise endlessly.

The goal is to build systems where agents can reason inside explicit, inspectable, and validated boundaries.

---

## One-Line Summary

Agentic programming is not the end of software engineering; it is an emerging discipline within it, where non-deterministic reasoning is wrapped inside deterministic, observable, and testable software systems.
