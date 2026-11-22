# Prototype Validation Methodology

## Math Intellect — Frozen Baseline and Current-State Boundary

**Project Lead:** Ngwe Htoon (Howard)  
**Document status:** Technical prototype-validation methodology for the frozen 51-case baseline.

## Purpose

The project has a documented technical evaluation covering **51 Cambridge IGCSE Mathematics test cases**, including text-based and visual/diagram-containing questions.

The evaluation examines:

- question interpretation;
- final mathematical answer;
- sub-question accuracy;
- solution completeness;
- assessment alignment;
- end-to-end LINE delivery.

This is technical prototype validation, not educational-impact or market validation.

## Frozen Baseline

| Metric | Reported result |
|---|---:|
| Total Test Cases | 51 |
| Text Interpretation Accuracy | 100.00% |
| Visual/Diagram Interpretation Accuracy | 4.17% |
| Overall Question Interpretation Success | 54.90% |
| Final Mathematical-Answer Accuracy | 95.65% |
| Overall Sub-question Accuracy | 76.62% |
| Average Solution Completeness | 77.78% |
| Average Assessment Alignment | 92.66% |
| Successful End-to-End LINE Response Rate | 90.20% |

The workbook and evidence files remain the source of record for denominators, applicability, scoring, and case-level evidence.

## Important Current-State Note

The current n8n Cloud deployment and later workflow-routing improvements postdate parts of the frozen validation evidence.

Current changes include:

- live n8n Cloud deployment;
- unsupported-input reply routing;
- Moderator Check failure routing to a user-facing safe reply;
- Quality Gate failure routing to a user-facing safe reply;
- continued testing of selected diagram-containing questions.

These changes **do not alter the frozen aggregate metrics above**.

A new aggregate result must come from a new versioned controlled evaluation.

## Evaluation Dimensions

| Dimension | What is checked |
|---|---|
| Question interpretation | Whether the task, givens, labels, subparts, and relevant diagram information match the source |
| Final answer | Whether the final mathematical answer is correct for applicable cases |
| Sub-question accuracy | Correctness at part level |
| Solution completeness | Sufficiency of required working |
| Assessment alignment | Whether generated guidance fits the demonstrated solution |
| LINE delivery | Whether the intended response reaches the user |

## Failure Classification

Record the earliest identifiable failure stage.

A quality-gate rejection is diagnostic evidence, not a successfully solved case.

Current user-facing failure messages improve interaction safety but do not convert failed cases into successful mathematical outputs.

## Diagram / Visual Boundary

The historical visual/diagram metric must not be hidden or reinterpreted.

The current system may successfully process selected diagram-containing questions, but no new aggregate diagram benchmark is claimed.

Rendered final visual-answer generation is a separate capability under development and should not be confused with interpretation of a diagram contained in the input question.

## Reproducibility

A reviewer should be able to trace:

```text
test case
→ source question
→ submitted image
→ workflow evidence
→ LINE output / failure
→ recorded score
```

New evaluations should be versioned rather than overwriting the frozen baseline.

## Evidence Files

- `validation/Math_Intellect_Prototype_Validation_Evidence_Record.pdf`
- `validation/Math_Intellect_Prototype_Validation_Record.xlsx`
- `validation/Math_Intellect_Prototype_Validation_Evidence_Record.pptx`

## Next Validation Stage

Future controlled evaluation should include:

- current cloud workflow;
- current failure-routing behavior;
- more diagram-containing questions;
- rendered-output cases when implemented;
- broader question diversity;
- independent mathematical checking.
