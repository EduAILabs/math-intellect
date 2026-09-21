# AI Workflow

## Math Intellect – AI-Assisted Mathematics Learning Platform

**Project Lead:** Ngwe Htoon (Howard)  
**Document status:** Implemented MVP workflow description, including current processing stages, known limitations, and clearly identified future extensions.

## Purpose

Math Intellect uses a sequential, task-specific workflow to turn an image submitted through LINE into a structured mathematics response. The processing stages separate question interpretation, mathematical reasoning, assessment review, consistency checking, quality review, and presentation. This design supports traceable review; it does not guarantee an error-free answer.

## End-to-End Processing Flow

```text
Student image submitted through LINE Official Account
    ↓
LINE Messaging API event → n8n webhook → image retrieval
    ↓
OpenAI vision-based image interpretation
    ↓
Question Analyzer → Solver → Examiner → Moderator → Quality Checker
    ↓
Formatter (JavaScript-based output assembly)
    ↓
LINE Messaging API → structured LINE response
```

The vision-processing and Question Analyzer responsibilities are related but distinct: image processing supplies extracted information, while the Question Analyzer interprets the mathematical task and structures information for the downstream stages. n8n orchestrates the sequence and passes structured information between stages.

## Six Processing Stages

| Stage | Defined responsibility | Intended output or check |
|---|---|---|
| 1. Question Analyzer | Reconstruct the question; identify topic, subtopic, given data, required results, and relevant contextual information. | Structured question interpretation for solution generation. |
| 2. Solver | Select an appropriate approach and generate mathematical steps, calculations, and final answers. | Step-by-step solution. |
| 3. Examiner | Review the method and answer from an assessment perspective. | Examiner-inspired assessment guidance, including relevant marking considerations. |
| 4. Moderator | Compare the interpreted question, solution, and assessment information for inconsistencies. | Consistency review and quality-gate information. |
| 5. Quality Checker | Review mathematical validity, solution completeness, clarity, and response structure. | Additional quality-review information. |
| 6. Formatter | Consolidate reviewed outputs using JavaScript and organize a concise response. | Student-facing text for LINE. |

The Examiner is the source for assessment-oriented guidance in the consolidated workflow; the Formatter presents the reviewed content rather than independently inventing assessment marks. Automated reviews may miss errors, so a quality-gate pass must not be interpreted as independent proof of correctness.

## Student-Facing Response Structure

| Part | Content |
|---|---|
| Header | Question analysis and assessment context. |
| Body | Step-by-step mathematical solution. |
| Tail | Examiner-inspired assessment guidance. |

The response structure is designed for LINE's mobile text interface. A more detailed PDF/email delivery route is **planned**, not an implemented MVP capability.

## Current Implementation

The functional MVP includes LINE image intake, webhook and image retrieval, OpenAI vision/language processing, the six-stage pipeline, JavaScript formatting, and LINE text delivery. It is orchestrated by locally hosted n8n, with ngrok providing development webhook access. The workflow has been tested end to end, but reliability varies by question type.

## Known Failure Modes and Boundaries

- Poor-quality images or missing diagram information can cause incorrect question interpretation before mathematical solving begins.
- A mathematically plausible solution may address an incorrectly reconstructed question; therefore, downstream correctness must not substitute for input verification.
- Moderator and Quality Checker stages provide additional review, not guaranteed mathematical proof or official examination marking.
- Retry requests for unusable images, production monitoring, and wider controlled validation require further development.
- Student information, tokens, raw webhook payloads, and credentials must not be included in public workflow exports or screenshots.

## Evidence and Related Documents

- [Root README — MVP and validation summary](../README.md)
- [System architecture](system-architecture.md)
- [Curriculum alignment](curriculum-alignment.md)
- [Quality assurance framework](quality-assurance.md)
- [Validation methodology](validation-methodology.md)

The repository may include a sanitized workflow export under `workflow/`; its availability and completeness must be checked separately from this design description.
