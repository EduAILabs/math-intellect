# Math Intellect — Product and System Specification

**Owner:** Ngwe Htoon (Howard)  
**Status:** Specification for the functional MVP  
**Last updated:** 2026-10-06

## 1. Purpose

Math Intellect is an AI-assisted mathematics learning platform that turns a
student's image-based question into a structured, examination-oriented response
delivered through LINE. The MVP is designed to extend access to mathematics
support outside classroom hours while keeping teachers central to learning and
assessment.

This document defines the current product boundary, expected behavior, quality
requirements, known limitations, and planned direction. It distinguishes
implemented MVP behavior from future work.

## 2. Product Principles

1. **Interpret before solving.** A plausible answer to a misread question is a
   failure.
2. **Show reasoning.** Responses should make the method understandable rather
   than return only a final answer.
3. **Separate responsibilities.** Interpretation, solving, assessment review,
   consistency checking, quality review, and formatting are distinct stages.
4. **Be curriculum-aware.** Terminology, depth, method, and assessment context
   should fit the relevant syllabus.
5. **Communicate uncertainty.** Automated checks reduce risk but do not prove
   correctness or constitute official examination marking.
6. **Protect learners and credentials.** Secrets, personal data, and private
   student submissions must not enter the public repository.

## 3. Users and Primary Use Cases

### Current users

- Students seeking guided help with an IGCSE Mathematics question.
- Teachers or tutors inspecting a structured solution and examiner-inspired
  assessment guidance.

### Primary MVP use case

1. A user sends a mathematics-question image to the
   Math Intellect LINE Official Account.
2. LINE sends an event to the n8n webhook.
3. The workflow retrieves and interprets the image.
4. Specialized stages analyze, solve, review, and format the response.
5. LINE delivers a structured text response to the user.

### Future use cases

Teacher dashboards, worksheet generation, PDF delivery, learner records,
analytics, institutional administration, multilingual support, and wider
curriculum coverage are planned and are not current MVP capabilities.

## 4. Current System Boundary

### Implemented

- LINE image-message intake and reply-token handling.
- n8n webhook orchestration and LINE image retrieval.
- OpenAI-assisted image interpretation and language processing.
- Question Analyzer, Solver, Examiner, Moderator, and Quality Checker stages.
- Moderator and quality-gate routing.
- JavaScript-based Formatter and LINE text delivery.
- A sanitized, inactive 15-node workflow export for technical inspection.
- A documented 51-case prototype-validation baseline.

### Development infrastructure

- n8n is locally hosted for the current prototype.
- ngrok exposes the webhook during development.
- OpenAI API and LINE Messaging API are external services.

### Not implemented or not demonstrated

- Production cloud deployment or production monitoring.
- Persistent learner accounts, records, or databases.
- Teacher dashboard or institutional administration.
- Production-ready retry and failure messaging for all rejected paths.
- Email/PDF delivery.
- Formal security, privacy, accessibility, or regulatory certification.
- Complete syllabus coverage or production-grade diagram interpretation.
- Proven learning outcomes, commercial traction, or institutional adoption.

## 5. Functional Architecture

```text
LINE image
  → Webhook
  → Event normalization and image check
  → Image download
  → Analyze Image
  → Question Analyzer
  → Solver
  → Examiner
  → Moderator
  → Moderator Check
  → Quality Checker
  → Quality Gate
  → Formatter
  → Reply to LINE
```

The six application stages are Question Analyzer, Solver, Examiner, Moderator,
Quality Checker, and Formatter. Intake, routing, and delivery nodes support those
stages. In the exported n8n workflow, the JavaScript node named `Formatter1`
implements the Formatter stage.

## 6. Stage Responsibilities and Contracts

| Stage | Responsibility | Required result |
|---|---|---|
| Analyze Image | Extract visible question content from the submitted image. | Faithful text/data extraction with no invented diagram facts. |
| Question Analyzer | Reconstruct the task and identify topic, givens, requested results, and context. | Structured interpretation suitable for downstream solving. |
| Solver | Select a suitable method and generate working and final answers. | Logically ordered, mathematically valid solution. |
| Examiner | Review the demonstrated method from an assessment perspective. | Examiner-inspired guidance consistent with the solution. |
| Moderator | Compare interpretation, solution, and assessment output. | Explicit consistency status and identified issues. |
| Quality Checker | Review correctness, completeness, clarity, and structure. | Explicit quality status and actionable issues. |
| Formatter | Assemble reviewed fields for the mobile interface. | Concise student-facing Header–Body–Tail response. |

The Examiner is the source of assessment-oriented guidance. The Formatter must
present reviewed content and must not independently invent marks.

## 7. Student-Facing Output Contract

The normal LINE response uses three logical sections:

| Section | Content |
|---|---|
| Header | Question interpretation and relevant assessment context. |
| Body | Step-by-step working and final answer. |
| Tail | Examiner-inspired assessment guidance. |

The response should be readable on a mobile device, preserve essential
mathematical working, clearly identify the final answer, and avoid claiming that
generated guidance is an official Cambridge mark scheme or certified grade.

## 8. Quality Requirements

Each material change must be evaluated against five dimensions:

1. **Input Integrity** — readable source and faithful reconstruction, including
   subparts, labels, and diagram facts.
2. **Curriculum Fit** — appropriate topic, terminology, method, depth, and
   calculator context.
3. **Mathematical Validity** — correct formulas, calculations, reasoning, units,
   and final answers.
4. **Assessment Consistency** — guidance fits the actual method and relevant
   assessment principles.
5. **Output Quality** — complete, clear, logically ordered, and suitable for LINE.

Automated moderation and quality gates are safeguards, not mathematical proof.
Objective comparison with the source question and an appropriate reference
remains necessary during validation.

## 9. Failure Behavior

The system should fail safely when an image is unreadable, required diagram
information is missing, structured output cannot be parsed, or a review stage
rejects the response.

Target behavior is to avoid presenting an unverified solution and to return a
clear retry or escalation message. The current sanitized workflow does not yet
provide user-facing responses on all false branches; this is a known MVP gap.

Failures must be classified by their earliest identifiable stage:

- intake or delivery;
- image interpretation;
- question analysis;
- mathematical reasoning;
- assessment alignment;
- moderation or quality review;
- formatting.

## 10. Security, Privacy, and Publication Requirements

- Never commit API keys, LINE tokens, channel secrets, live webhook identifiers,
  credential IDs, `.env` files, raw webhook payloads, reply tokens, user IDs, or
  private n8n exports.
- Use n8n credentials or environment-backed secrets, never hard-coded headers.
- Treat any exposed token as compromised; revoke and rotate it and remediate Git
  history where applicable.
- Do not publish identifiable student data or student submissions without an
  appropriate permission and privacy basis.
- Sanitize screenshots, exports, logs, documents, and sample payloads before
  publication.
- Use self-authored, licensed, or appropriately referenced question material.
  Do not reproduce protected papers or mark schemes beyond permitted use.
- State clearly that Math Intellect is independent and is not affiliated with or
  endorsed by Cambridge University Press & Assessment.

See [SECURITY.md](SECURITY.md) and [workflow/README.md](workflow/README.md).

## 11. Validation Baseline

The repository reports a frozen 51-case Cambridge IGCSE Mathematics technical
prototype-validation baseline. The workbook and supporting evidence are the
sources of record for exact denominators, applicability rules, calculations, and
case-level evidence.

Headline metrics must never be used outside their scope. In particular, final
answer accuracy among assessable outputs must not be presented as the probability
that any submitted image will be solved correctly. The reported 4.17% visual/
diagram interpretation result is a significant current limitation.

Any new validation cycle must:

- preserve the existing baseline instead of silently replacing it;
- assign versioned test-case identifiers;
- separate interpretation, reasoning, assessment, and delivery outcomes;
- document exclusions and non-applicable cases;
- retain an evidence chain from source question to recorded score; and
- report regressions and failures as well as successes.

See [docs/validation-methodology.md](docs/validation-methodology.md).

## 12. Acceptance Criteria for MVP Changes

A change is ready for review when:

- the exported workflow remains valid JSON and contains no credentials or
  personal data;
- the intended node connections and true/false branches have been inspected;
- affected success and failure paths have been tested in a separate development
  n8n instance using self-authored test material;
- mathematical output has been checked against an independent solution;
- LINE formatting and message-size behavior have been inspected;
- documentation distinguishes implemented behavior from planned behavior;
- relevant samples or validation records are updated without altering the frozen
  baseline; and
- a final secret and privacy scan finds no sensitive material.

Importing the public workflow successfully is useful evidence but does not by
itself establish end-to-end correctness.

## 13. Prioritized Product Requirements

### P0 — protect users and preserve the baseline

- Keep all public assets sanitized.
- Prevent rejected or incomplete outputs from being presented as verified.
- Preserve accurate, scoped validation claims.

### P1 — strengthen the MVP

- Improve visual and diagram interpretation.
- Add user-facing responses for unusable input and failed quality gates.
- Add structured error handling, retries, and observability.
- Expand controlled tests across question types.

### P2 — prepare for pilots

- Establish stable cloud hosting, access controls, logging, privacy processes,
  and cost monitoring.
- Add teacher review and feedback mechanisms.
- Evaluate usefulness separately from technical performance.

### P3 — future product expansion

- PDF delivery, teacher tools, persistent records, learning analytics,
  institutional administration, additional curricula, multilingual delivery, and
  broader STEM modules.

## 14. Sources of Truth

Use the narrowest authoritative source for each claim:

- Product status and public overview: [README.md](README.md)
- Current system boundary: [docs/system-architecture.md](docs/system-architecture.md)
- Stage behavior: [docs/ai-workflow.md](docs/ai-workflow.md)
- Public workflow implementation: [workflow/math-intellect-workflow-sanitized.json](workflow/math-intellect-workflow-sanitized.json)
- Sanitization and import notes: [workflow/README.md](workflow/README.md)
- Quality criteria: [docs/quality-assurance.md](docs/quality-assurance.md)
- Validation definitions and claims: [docs/validation-methodology.md](docs/validation-methodology.md)
- Roadmap status: [docs/roadmap.md](docs/roadmap.md)

When documents conflict, do not guess. Reconcile the discrepancy explicitly and
update all affected documents in the same change.
