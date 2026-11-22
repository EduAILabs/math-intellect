# Quality Assurance Framework

## Math Intellect – AI-Assisted Mathematics Learning Platform

**Project Lead:** Ngwe Htoon (Howard)  
**Document status:** Quality-assurance framework applied to MVP output review; not a guarantee of error-free responses, official marking, or production-grade reliability.

## Objective and Scope

Math Intellect uses a five-dimensional quality-assurance framework to review whether a submitted mathematics question has been interpreted accurately and whether its response is appropriate for the learner. The five dimensions originate in the project's portfolio and project report. They are **review criteria across the workflow**, not five additional executable AI nodes and not evidence that every response is error-free.

## Five Quality Dimensions

| Dimension | Review question | Typical evidence or failure indication |
|---|---|---|
| **Input Integrity** | Is the submitted image readable, and is the question—including diagram facts and subparts—captured correctly? | Source image compared with reconstructed question; missing labels or diagram relationships flagged. |
| **Curriculum Fit** | Are topic, terminology, method, depth, assessment context, and calculator restrictions suitable for the relevant syllabus? | Syllabus reference and educator review; unsupported or inappropriate method flagged. |
| **Mathematical Validity** | Are equations, calculations, reasoning steps, formulas, diagram interpretations, and final answers correct? | Worked-solution comparison and mathematical checking; wrong values or unjustified steps flagged. |
| **Assessment Consistency** | Is the examiner-inspired guidance broadly consistent with the actual method, answer, relevant assessment objectives, and marking principles? | Assessment review against the interpreted question and permitted reference material; inconsistent marks or claims flagged. |
| **Output Quality** | Is the response complete, clear, logically sequenced, appropriately formatted, and understandable in LINE? | Rendered LINE output reviewed for missing parts, unclear symbols, omissions, and delivery issues. |

## How the Framework Maps to the Workflow

```text
Image intake and Question Analyzer → Input Integrity
Question interpretation and Solver → Curriculum Fit
Solver, Moderator and Quality Checker → Mathematical Validity
Examiner and Moderator → Assessment Consistency
Quality Checker and Formatter → Output Quality
```

This is a conceptual mapping; it does not imply separate automated checks exist for every item in the table. The Moderator checks consistency across intermediate outputs, the Quality Checker performs an additional review, and the JavaScript Formatter constructs the LINE-facing text. The system's assessment information is consolidated from the Examiner's output rather than independently invented by the Formatter.

## Quality Gate and Failure Handling

The design includes moderation, checking, and a quality-gate approach intended to identify inconsistent or unsuitable responses before delivery. However, automated review cannot substitute for comparison against the original question or independent human assessment. In particular, a response can appear internally consistent while relying on an incorrect image interpretation.

The current project identifies an improved user-facing retry request for unreadable or incomplete images as **future development**. No general claim is made that all failures are intercepted, automatically resolved, or safely escalated in the present MVP.

## Evidence and Interpretation

The documented validation record includes interpretation results, final-answer and sub-question accuracy, solution completeness, assessment alignment, and end-to-end LINE delivery. These are distinct measurements. **LINE delivery success measures completion of the delivery flow, not mathematical correctness**; final-answer accuracy, completeness, and assessment alignment each examine a different aspect of output quality.

The recorded visual/diagram interpretation result of **4.17%** identifies a serious current limitation. Accordingly, a successful downstream review must not be generalized into a claim of reliable visual problem understanding or production-grade robustness. Refer to the validation record for per-case scoring and denominators.

## Educational and Operational Safeguards

Before broader learner or school use, the project needs controlled pilots, educator oversight for assessment-sensitive applications, student privacy safeguards, clear disclosure of AI limitations, and stronger failure-handling/monitoring procedures. These are development requirements, not claims of existing institutional deployment.

## Related Documents

- [Curriculum alignment](curriculum-alignment.md)
- [AI workflow](ai-workflow.md)
- [Validation methodology](validation-methodology.md)
- [System architecture](system-architecture.md)
- [Root README](../README.md)
