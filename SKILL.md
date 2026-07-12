---
name: reverse-motivation-paper-reading
description: Reconstruct machine-learning and time-series papers from motivation rather than section-by-section summary. Use when reading an attached paper, PDF, preprint, or method description to explain why each component was introduced, which failure it repairs, what assumptions it relies on, and how the final method forms as a problem–baseline–failure–repair chain.
---

# Reverse Motivation Paper Reading

## Overview

Use a causal reading order: identify the original training or modeling problem, derive the simplest plausible solution, expose where it fails during optimization or deployment, then explain each paper component as a targeted repair. Produce an intuitive explanation first and preserve the paper's exact mechanism, evidence, and limitations separately.

## Workflow

### 1. Establish the target and hidden assumption

Extract the task objective, undesirable behavior, and assumption that makes the standard baseline appear sufficient. State the unit of difficulty precisely: sample, time step, channel, label, optimization stage, or distribution shift.

### 2. Derive the minimal baseline

Construct the most natural intervention before reading the full architecture. Describe what it changes in the objective, information flow, or data selection, and what behavior it is intended to induce.

### 3. Find the first failure

Trace the training or inference timeline. Ask when the baseline's signal becomes unreliable, what observable symptom appears, and which useful behavior is harmed. Phrase this as a causal bug, not as a vague limitation.

### 4. Map the first repair

Explain the added component as a patch: input signal, operation, changed gradient or information path, and repaired failure. Distinguish persistent state or memory from merely recomputed statistics. Do not claim that a component tracks individual samples unless the paper explicitly does so.

### 5. Search for residual failure and additional patches

For every repair, identify its remaining dependency or new risk: estimator bias, instability, compute cost, underfitting, leakage, or sensitivity. Explain later modules only as responses to those residual problems. Keep independent mechanisms separate.

### 6. Reconstruct the final chain

Use the compact form:

```text
original problem → minimal solution → failure A → repair A
→ residual failure B → repair B → final framework
```

For each link, label the evidence level: explicit claim in the paper, experimentally supported observation, or interpretation/inference.

## Required output

Lead with a short intuitive narrative, then provide:

- the problem–failure–repair chain;
- a mechanism table with component, input signal, operation, repaired failure, and unresolved risk;
- the final objective or information flow when equations are necessary;
- ablation evidence showing which repair contributes what;
- assumptions, transfer risks, and modules that can be removed or replaced in the user's task.

Use concrete language such as “loss becomes an unreliable predictability proxy after overfitting” rather than merely repeating names such as “predictability evolution.” Avoid anthropomorphic claims unless immediately translated into the actual update rule.

## Quality checks

Before finalizing, verify that every module answers “which failure forced its introduction?”, that the explanation does not turn stage-wise recomputation into sample-level memory, and that mutual-model mechanisms are described according to the direction and timing of information flow. Separate the paper's demonstrated result from any proposed adaptation to the user's application.
