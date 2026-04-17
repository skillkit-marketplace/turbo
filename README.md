# Quick Iteration Agent Skill

Fast iteration workflow with mandatory subagent plan review. Designed for implementing small-to-medium changes quickly without sacrificing technical integrity.

## Overview

The `quick-iteration` skill enforces a structured **Plan -> Review -> Implement** cycle. It bridges the gap between "cowboy coding" and full architectural ceremony, ensuring that even "simple" changes are verified by an independent reviewer before execution.

**Use this when:**
- Implementing small-to-medium changes (UI tweaks, bug fixes, logic updates).
- The goal is clear and doesn't require architectural decisions.
- Speed is important, but accuracy is non-negotiable.

**Avoid when:**
- Starting new features or systems from scratch.
- Making high-level architectural decisions.
- Requirements are ambiguous or require deep brainstorming.

## The 5-Step Flow

1.  **Capture Intent:** Restate the goal in 1-2 sentences to ensure alignment.
2.  **Write Brief Plan:** Create a 3-5 bullet plan covering **What**, **Where**, **How**, and **Test**.
3.  **Dispatch Reviewer:** Use a subagent to review the plan using the `validate-plan` skill.
4.  **Fix Issues:** Address CRITICAL and WARNING findings from the review.
5.  **Implement:** Execute the reviewed plan exactly as stated.

## Hard Gates

> **IMPORTANT:** Do NOT write a single line of implementation code until:
> 1.  A brief plan (3-5 bullets) has been written.
> 2.  A subagent reviewer has returned **NO CRITICAL issues**.

## Project Structure

- `SKILL.md`: Core logic and rules for the quick-iteration workflow.
- `references/plan-format.md`: Detailed guide on writing valid brief plans with examples.
- `references/reviewer-dispatch.md`: Template and instructions for dispatching the subagent reviewer.

## Why the Reviewer?

Confidence is often where silent bugs live. By dispatching a subagent reviewer, we:
- Remove sunk-cost bias from the implementation plan.
- Catch DRY/YAGNI violations early.
- Identify missing edge cases before they are encoded.
- Save time by preventing post-implementation rework.

