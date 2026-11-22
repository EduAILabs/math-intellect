# Quality Assurance

## Math Intellect — Current MVP

Math Intellect uses multiple review stages to reduce avoidable errors before a normal response is returned through LINE.

Automated quality checks are safeguards, not independent proof of correctness.

## Five Quality Dimensions

| Dimension | Review question |
|---|---|
| Input Integrity | Was the question and relevant visible information interpreted correctly? |
| Curriculum Fit | Is the method and terminology appropriate for the intended syllabus context? |
| Mathematical Validity | Are calculations, reasoning, formulas, and final answers correct? |
| Assessment Consistency | Does the examiner-inspired guidance match the demonstrated solution? |
| Output Quality | Is the response clear, complete, concise, and suitable for LINE? |

## Implemented Review Flow

```text
Solver
→ Examiner
→ Moderator
→ Moderator Check
→ Quality Checker
→ Quality Gate
```

### Moderator failure

```text
Moderator Check (false)
→ Review Failure Reply
→ Reply to LINE
```

### Quality failure

```text
Quality Gate (false)
→ Review Failure Reply
→ Reply to LINE
```

### Approved output

```text
Quality Gate (true)
→ Formatter1
→ Reply to LINE
```

## Unsupported Input Handling

The workflow also includes an earlier input check:

```text
If (false)
→ Unsupported Input Reply
→ Reply to LINE1
```

This provides user-facing feedback when the incoming message is not a supported mathematics-question image.

## Important Boundary

The current workflow now has user-facing messages for:

- unsupported input;
- Moderator Check failure; and
- Quality Gate failure.

It does **not** yet provide production-grade recovery for every possible API, network, timeout, malformed-model-output, or infrastructure failure.

## Diagram / Visual Output

Diagram-containing input questions can be processed when the information is successfully interpreted.

If the final answer requires a rendered visual, the current stable MVP provides text-based drawing instructions. Rendered image output remains under development.

## Validation Boundary

The frozen 51-case validation baseline identified a serious historical visual/diagram interpretation limitation. Those metrics remain unchanged.

Later workflow changes, cloud deployment, and selected successful tests do not constitute a new aggregate validation result.

## Before Broader Use

Further work is needed for:

- wider regression testing;
- stronger monitoring and observability;
- privacy and retention processes;
- access control;
- educator review of assessment-sensitive use;
- additional validation of diagram and graphical questions;
- rendered visual-answer generation;
- institution-level safeguards.
