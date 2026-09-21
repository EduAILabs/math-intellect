# Math Intellect — Sample Demonstrations

This folder contains selected question-input and response-output examples from the Math Intellect functional MVP.

## Sample Index

| Sample | Type | Evidence | Outcome |
|---|---|---|---|
| 01 — Linear Equation | Text-based algebra | [Question](sample-question-01.md) · [Output](sample-output-01.md) | Successful end-to-end demonstration |
| 02 — Right-Triangle Trigonometry | Diagram-based trigonometry | [Question](sample-question-02.md) · [Output](sample-output-02.md) | Documented failure case |

## Notes on Sample 01

Sample 01 demonstrates successful end-to-end processing of a text-based algebra question. The system returned a structured LINE response including question classification, step-by-step working, a final answer, and examiner-inspired assessment guidance.

## Notes on Sample 02

Sample 02 documents a diagram-dependent failure case.

In this test:

- the written instruction was extracted, but the mathematical information encoded in the diagram was not successfully captured for downstream use;
- the Solver reported that it could not see the diagram and did not produce a mathematical solution;
- the Moderator returned a `FAIL` status; and
- the Moderator Check node routed the item to the **False Branch** rather than the PASS branch, so the normal PASS-based delivery path was not followed.

This sample is included to illustrate a current limitation of the functional MVP in diagram-dependent question handling.

## Evidence Notes

Sample questions are self-authored or used with appropriate permission.

Generated outputs and workflow observations are recorded from actual MVP interactions and reviewed against independent mathematical expectations where appropriate.

These selected examples illustrate system behaviour. They do not replace the project’s 51-case technical validation record, nor do they establish measured educational impact.

For the complete project overview, see the [Project README](../README.md).
