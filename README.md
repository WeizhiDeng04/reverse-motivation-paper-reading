# reverse-motivation-paper-reading

A reusable paper-reading skill for reconstructing how a research method forms from its motivation.

Instead of summarizing a paper section by section, this skill explains the method as a causal chain:

```text
motivation / pain point
→ minimal baseline
→ baseline failure
→ targeted patch
→ residual failure
→ next patch
→ final framework
```

It is especially useful for machine learning, time-series forecasting, model training methods, and papers where the architecture looks like a pile of modules until you ask which failure each module repairs.

## What this skill is for

Use it when you want to:

- understand why a method was designed this way;
- explain a paper from the author's original difficulty rather than from the final architecture;
- separate necessary mechanisms from cosmetic complexity;
- train research taste by predicting what patch should naturally follow from a failure case;
- adapt a paper's method to your own setting by deciding which modules are transferable.

## Core reading pattern

The skill asks four recurring questions:

1. What problem made the obvious baseline attractive?
2. When does that baseline break?
3. Which module repairs that exact breakage?
4. What new risk or residual failure remains after the patch?

This turns a paper into a formation story rather than a feature list.

## Example prompt

```text
Use reverse-motivation-paper-reading to explain this paper.
Focus on how the method forms from motivation:
problem → baseline → bug → patch → remaining bug → final framework.
```

## Optional idea-taste drill

For training research taste, use the skill in an active mode:

1. Read only the abstract, introduction, and motivation.
2. Pause and predict the simplest method you would design.
3. Read the actual method.
4. Compare your predicted patch with the authors' patch.
5. Record what failure you missed, whether the authors' module was natural, and which design pattern transfers to future papers.

The goal is not just to understand one paper. The goal is to improve your intuition for which technical moves are natural, necessary, over-designed, or ad hoc.

