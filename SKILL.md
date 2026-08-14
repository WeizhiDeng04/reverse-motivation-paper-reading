---
name: reverse-motivation-paper-reading
description: Reconstruct machine-learning and time-series papers from motivation rather than section-by-section summary. Use when reading an attached paper, PDF, preprint, or method description to explain why each component was introduced, which failure it repairs, and what assumptions and limitations it relies on.
---

# Reverse Motivation Paper Reading

## Overview

Use a causal reading order: identify the original training or modeling problem, derive the simplest plausible solution, expose where it fails during optimization or deployment, then explain each paper component as a targeted repair. Produce an intuitive explanation first and preserve the paper's exact mechanism, evidence, and limitations separately.

## Workflow

### 1. Establish the target and hidden assumption

Extract the task objective, undesirable behavior, and assumption that makes the standard baseline appear sufficient. Take the papers on time series prediction tasks as an example, precisely stating the difficult measurement units: samples, time steps, channels, labels, optimization stages or distribution shifts.

### 2. Derive the minimal baseline / MVP

Construct the most natural intervention before reading the full architecture. Describe what it changes in the objective, information flow, or data selection, and what behavior it is intended to induce.

### 3. Find the first failure

Trace the training or inference timeline. Ask when the baseline's signal becomes unreliable, what observable symptom appears, and which useful behavior is harmed. Phrase this as a causal bug, not as a vague limitation.

### 4. Map the first repair

Explain the added component as a patch: input signal, operation, changed gradient or information path, and repaired failure. Distinguish persistent state or memory from merely recomputed statistics. Do not claim that a component tracks individual samples unless the paper explicitly does so.

### 5. Search for residual failure and additional patches

For every repair, identify its remaining dependency or new risk: estimator bias, instability, compute cost, underfitting, leakage, or sensitivity. Explain later modules only as responses to those residual problems. Keep independent mechanisms separate.

## Required output

Lead with a short intuitive narrative, then provide:

- a mechanism table with component, input signal, operation, repaired failure, and unresolved risk;
- the final objective or information flow when equations are necessary;
- ablation evidence showing which repair contributes what;
- assumptions, transfer risks, and modules that can be removed or replaced in the user's task.

Use concrete language such as “loss becomes an unreliable predictability proxy after overfitting” rather than merely repeating names such as “predictability evolution.” Avoid anthropomorphic claims unless immediately translated into the actual update rule.

## Quality checks

Before finalizing, verify that every module answers “which failure forced its introduction?”, that the explanation does not turn stage-wise recomputation into sample-level memory, and that mutual-model mechanisms are described according to the direction and timing of information flow. Separate the paper's demonstrated result from any proposed adaptation to the user's application.

## Supplementary Requirements Explanation

- Think about each point carefully, that is, why this method is chosen and not others (do not blindly praise, view it dialectically, because there are some points that actually have problems). This point is used to help readers discover the limitations or areas for improvement in the paper, or to correct some unnecessary improvement ideas that readers may have.
- All analyses are based on your complete reading of the PDF paper. Do not write in Markdown if you haven't finished reading it. In Markdown, there must be a mapping to the original text, such as formula numbers or subheadings. This is used to help readers establish the connection between Markdown and the original paper text.
