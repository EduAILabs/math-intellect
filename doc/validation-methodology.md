# Prototype Validation Methodology

## Math Intellect – AI-Assisted Mathematics Learning Platform

**Project Lead:** Ngwe Htoon (Howard)  
**Document status:** Technical prototype-validation methodology and reported baseline; not evidence of educational impact, market validation, complete syllabus coverage, or production readiness.

## Purpose and Evidence Boundary

The MVP has a documented technical evaluation covering **51 Cambridge IGCSE Mathematics test cases**, including text-based and visual/diagram-containing questions. The tests examine interpretation, mathematical answers, solution completeness, assessment alignment, and LINE delivery. This is **prototype technical validation**; it is not an educational outcome study, market validation, proof of complete syllabus coverage, or evidence of production readiness.

This document explains the evaluation dimensions and how to interpret the figures published in README V4.0. The frozen test-case workbook and accompanying evidence are the sources of record for individual scores, inclusion rules, denominators, and calculation formulas. This narrative must not be used to replace those source records.

## Test Case and Evidence Chain

The documented process connects a test-case ID, source-question reference, the image supplied to LINE, expected mathematical interpretation, AI interpretation, generated solution, assessment review, LINE output or failure evidence, and scores recorded in the workbook. Where an applicable official question or marking reference is used for private evaluation, retain a precise bibliographic reference and respect permissions and copyright in public evidence.

An evidence item should make it possible to distinguish a problem in **image interpretation** from a problem in **reasoning**, **assessment**, or **delivery**. A generic screenshot showing a successful n8n run does not, by itself, establish which question was tested or whether its mathematical answer was correct.

## Evaluation Dimensions

| Dimension | What the evaluator checks | Important distinction |
|---|---|---|
| Question interpretation | Whether the reconstructed task, givens, required answer, and relevant diagram information match the source. | Text-only and visual/diagram questions should be reported separately. |
| Final mathematical answer | Whether the final answer is correct under the workbook's applicable-case criteria. | Do not present a conditional answer rate as success over all 51 cases without verifying the denominator. |
| Sub-question accuracy | Whether individual question parts are correct under the recorded part-level scoring. | May have a different denominator from case-level final-answer accuracy. |
| Solution completeness | Whether the required reasoning and working are sufficiently represented under the documented rubric. | Distinct from having a correct final answer. |
| Assessment alignment | Whether the generated assessment guidance fits the demonstrated solution and reference expectations under the documented rubric. | Does not certify an official Cambridge mark scheme or grade. |
| End-to-end LINE success | Whether an intended response is successfully delivered through the full interaction. | Delivery success is not a mathematical-correctness result. |

For completeness and assessment alignment, preserve the workbook's recorded rating scale, weightings, and treatment of non-applicable results when reporting averages. Do not silently count N/A as zero, assume all metrics use the same denominator, or infer unstated formulas from rounded percentages.

## Published Baseline Results

The following figures reproduce the **frozen README V4.0 summary**; they are reported values, not independently recomputed figures in this Markdown document.

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

**Interpretation warning:** The high final-answer percentage must not be described as the probability that *any* submitted question will be answered correctly. Overall question interpretation is 54.90%, while visual/diagram interpretation is only 4.17%; those results show why metric scope and failure-stage reporting matter. Exact denominators, applicability conditions, score normalization, and rounding should be read from the workbook before further numerical claims are made.

## Failure Classification and Missing Outputs

When a question is interpreted incorrectly or required diagram information cannot be retrieved, record the earliest identifiable failure stage and retain supporting evidence. If a failed workflow produces no evaluable final solution or assessment, use the workbook's defined non-applicable status rather than inventing scores. Record LINE success separately from answer accuracy, solution completeness, and assessment alignment.

The Moderator and Quality Checker may flag issues, but quality-gate outcomes are not a substitute for objective comparison with the question and reference answer. A failure that is correctly identified by a gate is valuable diagnostic evidence, not a successful solved response.

## Reproducibility and Reviewer Use

A reviewer should be able to locate the same test-case identifier across the workbook and evidence, inspect the original question reference and relevant screenshots, and trace the recorded result. The detailed record should document sample composition, metric calculation, scoring decisions, exclusions, and failure modes. Any revised test set should be versioned rather than silently replacing the frozen V3.0 baseline.

### Evidence files expected in the repository

- [Prototype Validation Evidence Report (PDF)](../validation/Math_Intellect_Prototype_Validation_Evidence_Record_V3.0.pdf)
- [Prototype Validation Record (XLSX)](../validation/Math_Intellect_Prototype_Validation_Record_V3.0.xlsx)
- [Prototype Validation Evidence Slides (PPTX)](../validation/Math_Intellect_Prototype_Validation_Evidence_Record_V3.0.pptx)

**Publication check:** The links above are intended repository paths. They will work only when the corresponding files have been uploaded with these exact names. Before making the repository public, review screenshots and past-paper/mark-scheme extracts for personal information, secrets, and reproduction permissions. The PDF is the preferred quick-review format; the workbook provides the underlying scoring record.

## Next Validation Stage

Future work should prioritize diagram interpretation, expand the question sample, clarify failure handling, and independently check accuracy and assessment claims. A separate consent-based learner/teacher pilot would be needed to evaluate educational usefulness, learning outcomes, workload, accessibility, and safety in practice.

## Related Documents

- [Root README — published baseline](../README.md)
- [Quality assurance](quality-assurance.md)
- [AI workflow](ai-workflow.md)
- [Curriculum alignment](curriculum-alignment.md)
- [Educational impact and proposed study](educational-impact.md)
