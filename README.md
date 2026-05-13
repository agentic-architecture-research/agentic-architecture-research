# Agentic Architecture Research

Agentic Architecture Research is a research and build hub for exploring how reliable agentic systems should be designed, composed, validated, and executed.

The current focus is building a **plugin-harness runtime**: an open-source, local-first control plane for programming agentic workflows with plugins.

Originally, this profile explored individual harness pieces such as intent routing, atomic tasks, context injection, validation loops, and knowledge indexes as separate research tracks. Those ideas still matter, but the direction has evolved:

> The plugin-harness runtime is now the foundation.
> Research ideas become plugins that run on top of it.

---

## Core Thesis

Current discourse often treats AI agents as a magical departure from traditional software.

Our foundational thesis is the opposite:

> Agentic programming is the next logical abstraction layer in software engineering.

We are moving away from hand-writing every step of logic and toward designing systems that translate intent into executable, inspectable, and verifiable workflows.

A useful way to conceptualize this layer is:

```txt
Intent → Execution Graph → Validation Loop
```

The harness runtime exists to make that architecture programmable.

---

## What We Are Building

We are building a local-first runtime for composing agentic workflows from plugins.

The runtime is not the agent.

The runtime is the control plane around agents, tools, validators, planners, context systems, and execution backends.

A simple mental model:

```txt
workflow file = program
plugin = callable module
plugin manifest = function signature and metadata
input/output schema = type contract
runtime = interpreter / executor
artifact store = durable workflow state
event log = execution trace
inspect/replay/diff = debugging tools
```

The goal is to let developers define workflows like:

```txt
Run this plugin.
Pass its output to the next plugin.
Validate the result.
Store artifacts.
Log every step.
Replay or diff the run later.
```

---

## Why Plugins

Agentic workflows should not be trapped inside one monolithic harness.

Different users will want different:

* agents
* models
* planners
* executors
* validators
* context systems
* repository structures
* approval gates
* debugging tools
* CI/CD flows

The harness runtime should provide the stable layer that allows those pieces to be composed safely and predictably.

The runtime should be opinionated about **contracts**, not plugin internals.

```txt
Runtime controls:
connection, validation, execution boundary, result shape, artifacts, logs, permissions

Plugin controls:
internal logic, model choice, API calls, tools used, algorithms, strategy
```

This makes plugins replaceable, inspectable, testable, and reusable.

---

## The Core Problem: A Shift Toward Constraints

Current AI workflows rely heavily on open-ended prompt engineering, large context windows, and manual human supervision.

These approaches scale poorly.

LLMs are non-deterministic. Left unconstrained, this leads to unpredictable behavior, escalating cost, and systems that are difficult to debug.

To build reliable agentic software, engineering pressure naturally pushes toward structure:

* explicit plugin contracts
* typed inputs and outputs
* deterministic workflow execution
* bounded task scope
* clear success/reject/error states
* durable artifacts
* append-only event logs
* replayable runs
* diffable workflow behavior

The goal is not to eliminate non-determinism.

The goal is to contain it inside a structured runtime.

---

## Runtime Model

The harness runtime is built around this flow:

```txt
Plugin Contracts
  → Workflow Composition
  → Validation
  → Execution
  → Artifacts + Events
  → Inspection / Replay / Diff
  → Plugin Ecosystem Readiness
```

The runtime should be able to:

* load plugins
* validate plugin manifests
* validate workflow files
* resolve plugin IDs and versions
* validate input and output schemas
* execute workflow steps in graph order
* route success, reject, and error outcomes
* store artifacts locally
* write structured event logs
* inspect previous runs
* replay from a step
* diff two runs
* swap plugin implementations without rewriting the runtime

---

## Research Plugins

Research in this profile now feeds into the plugin ecosystem.

Instead of treating every idea as a separate harness, each research area can become a plugin or set of plugins that runs on the common runtime.

Examples:

* intent router plugin
* atomic task planner plugin
* repo knowledge index plugin
* context injection plugin
* validator plugin
* local shell executor plugin
* test runner validator plugin
* coding-agent adapter plugin
* GitHub workflow plugin
* language-specific context plugin

This gives the research a shared foundation.

The runtime provides the control plane.

The plugins provide the research capabilities.

---

## Active Research Areas

This profile explores architecture for reliable agentic systems, especially:

* plugin-based agentic workflows
* deterministic control planes
* workflow graphs and runtime-owned state
* plugin contracts and manifest validation
* schema-based input/output validation
* atomic task decomposition
* scoped context injection
* repository knowledge indexes
* artifact-based execution traces
* inspectable and replayable runs
* run diffing for non-deterministic workflows
* validation loops around agent outputs
* local-first developer tooling
* future harness language readiness

---

## Engineering Principles

### 1. Runtime over monolith

The goal is not to build one fixed end-to-end agent workflow.

The goal is to build the runtime that lets users compose their own workflows.

### 2. Contracts over internals

The runtime should validate what a plugin declares, receives, and returns.

It should not dictate how the plugin performs its work internally.

### 3. Deterministic control plane

Agents may propose plans or generate outputs, but the runtime owns execution order, state transitions, routing, artifacts, and logs.

### 4. Inspectability by default

Every run should produce artifacts and events that make the workflow understandable after execution.

### 5. Local-first development

The early runtime should be useful locally before any cloud dashboard, marketplace, or hosted registry exists.

### 6. Research becomes plugins

Research ideas should become composable plugins that can be tested, swapped, improved, and reused through the runtime.

---

## Near-Term Build Focus

The immediate build focus is the open-source plugin-harness runtime.

Priority modules:

1. Plugin boundary and contract
2. Workflow language / workflow IR
3. Validation system
4. Plugin registry and resolution
5. Runtime execution engine
6. Artifact store and event log
7. Developer CLI and debugging tools
8. Plugin authoring tools

The first version should prove that a developer can:

* define a workflow
* register mock plugins
* validate the workflow
* run the workflow
* inspect the run
* replay from a step
* diff two runs
* swap one plugin implementation
* write a simple plugin against the documented contract

---

## Long-Term Direction

The long-term direction is a plugin ecosystem for agentic workflows.

The sequence is:

```txt
Open-source runtime
→ local plugin system
→ useful first-party research plugins
→ public plugin registry
→ verified plugins
→ paid plugin marketplace
```

The marketplace is not the starting point.

The runtime must earn trust first.

---

## Status

This is an active research and build profile.

Expect rapid iteration, experimental repositories, and evolving architecture.

The current center of gravity is clear:

> Build the plugin-harness runtime first.
> Build research-based plugins on top of it.
