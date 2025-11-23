# Amplifier System Summary

## 1. Overview

Amplifier is a "Metacognitive AI Development" system designed to automate complex workflows by describing how to think through them. It uses "recipes" (metacognitive processes) to build tools that combine deterministic code with AI intelligence.

**Core Philosophy:**

- **Code for Structure:** Control flow, state management, persistence.
- **AI for Intelligence:** Understanding, reasoning, extraction.
- **Amplification:** Combining both to achieve more than either alone.

## 2. Architecture

### 2.1. Components

- **Claude Code SDK Toolkit (`ccsdk_toolkit`):** The core library for building AI tools. It provides patterns for pipeline, parallel, and hierarchical composition.
- **Agents:** Specialized AI personas (e.g., `zen-architect`, `bug-hunter`) defined in `AGENTS.md` and `.claude/agents/`.
- **CLI:** Tools to run workflows and manage the system.

### 2.2. Directory Structure

- **`amplifier/`**: Core library components and SDK.
- **`scenarios/`**: Production-ready tools with complete documentation.
- **`ai_working/`**: Experimental tools and prototypes.
- **`docs/`**: Documentation (proposed to be consolidated).

### 2.3. Key Patterns

- **Decomposition:** Breaking large tasks into small, focused AI microtasks.
- **Incremental Saving:** Persisting results after each step.
- **Parallel Processing:** Running independent AI tasks concurrently.
- **Graceful Degradation:** Handling partial failures in batch processing.
- **Flow-Driven Development:** Validate real user flows after each chunk of work. "If you can't verify the user flow works, don't ship it."

## 3. Usage

### 3.1. Creating Tools

Tools are created by defining a "recipe" (step-by-step thinking process) and implementing it using the SDK.

- **Template:** `amplifier/ccsdk_toolkit/templates/tool_template.py`
- **Workflow:** Plan -> Docs -> Code -> Verify.

### 3.2. SDK Usage

The SDK allows programmatic control over Claude Code.

```python
# Example Pattern
async def process_data(data):
    chunks = prepare_data(data)
    results = await asyncio.gather(*[ai_analyze(chunk) for chunk in chunks])
    save_results(results)
    return await ai_synthesize(results)
```

## 4. Case Study: `umersami-me`

This repository demonstrates using Amplifier for personal branding and resume generation.

### 4.1. Resume Generation

- **Master Source:** `ai_working/resume_master.md` contains the comprehensive resume content.
- **Process:**
  - The master resume serves as the single source of truth.
  - Scripts (likely in `ai_working/`) generate tailored versions (e.g., for specific job applications) from this master.
  - It highlights the "AI-first" workflow, mentioning usage of Claude Code and subagents.

### 4.2. Structure

- **`agents/`**: Custom agents for the project.
- **`ai_working/`**: Active working directory for resumes and workflows.
- **`docs/`**: Project-specific documentation.

## 5. Evolve-Mind Implementation Plan (Preliminary)

The goal is to implement `evolve-mind` using Amplifier as an SDK/API.

### 5.1. Integration Strategy

- **Dependency:** Add `amplifier` as a submodule or package dependency.
- **SDK Usage:** Import `ccsdk_toolkit` to build intelligent features.
- **Structure:** Follow the `scenarios/` pattern for `evolve-mind` tools.

### 5.2. Next Steps

1.  Gain access to `evolve-mind` repository.
2.  Initialize Amplifier SDK integration.
3.  Define the core "recipes" for `evolve-mind`.
