# Math Intellect — Product and System Specification

**Owner:** Ngwe Htoon (Howard)  
**Status:** Current specification for the cloud-deployed functional MVP  
**Last updated:** 2026-11-22

## 1. Purpose

Math Intellect is an AI-assisted mathematics learning platform that converts a mathematics-question image submitted through LINE into a structured, assessment-oriented text response.

The current stable MVP is deployed on n8n Cloud and connected to the Math Intellect LINE Official Account. This specification defines the implemented reviewer-facing behavior, failure routing, known limitations, and future boundaries.

## 2. Product Principles

1. Interpret before solving.
2. Show meaningful mathematical reasoning.
3. Separate interpretation, solving, assessment, moderation, quality checking, formatting, and delivery.
4. Remain curriculum-aware without claiming official examination authority.
5. Fail safely when the current review gates do not approve an answer.
6. Keep secrets, private user data, and operational credentials out of the public repository.
7. Distinguish current live-MVP deployment from future production SaaS or institutional deployment.

## 3. Current Users and Use Case

### Current users

- Students seeking structured help with mathematics questions.
- Teachers or tutors reviewing generated working and examiner-inspired guidance.
- Technical/reviewer users evaluating the current MVP.

### Primary use case

1. User submits a mathematics-question image to the Math Intellect LINE Official Account.
2. LINE sends the event to the n8n Cloud webhook.
3. The workflow checks that the incoming message is a supported image input.
4. The image is retrieved and interpreted.
5. Question Analyzer, Solver, Examiner, Moderator, and Quality Checker process the question.
6. Review gates determine whether a normal answer can be returned.
7. Formatter assembles the reviewed response.
8. LINE returns either the structured answer or a safe fallback message.

## 4. Current System Boundary

### Implemented

- LINE image-message intake.
- n8n Cloud webhook orchestration.
- LINE image retrieval.
- OpenAI-assisted image interpretation and language processing.
- Question Analyzer.
- Solver.
- Examiner.
- Moderator.
- Moderator Check.
- Quality Checker.
- Quality Gate.
- JavaScript Formatter.
- Normal LINE response.
- Unsupported-input user response.
- Review-failure user response.
- Public sanitized workflow export.
- Public technical documentation.
- Frozen 51-case validation baseline.
- Live reviewer testing through LINE.

### Current deployment

- The reviewer-facing stable MVP is deployed on **n8n Cloud**.
- The n8n workspace/editor is private.
- LINE is the public user-facing interface.
- GitHub provides sanitized technical evidence.
- Local development continues separately for experimental features, including rendered visual-answer generation.

### Not implemented as a current production capability

- Institution-ready SaaS operations.
- Persistent learner accounts or databases.
- Teacher dashboard.
- Production-grade monitoring and service guarantees.
- Institutional administration.
- Formal security/privacy/compliance certification.
- Proven educational outcomes or commercial traction.
- Automatic final rendered images for answers that require a diagram, graph, construction, transformation, or similar visual.

## 5. Functional Architecture

```text
LINE message
  → Webhook
  → Edit Fields
  → If (image check)

If TRUE:
  → Download Image
  → Analyze Image
  → Edit Fields1
  → Question Analyzer
  → Solver
  → Examiner
  → Moderator
  → Moderator Check

Moderator Check TRUE:
  → Quality Checker
  → Quality Gate

Quality Gate TRUE:
  → Formatter1
  → Reply to LINE

Moderator Check FALSE:
  → Review Failure Reply
  → Reply to LINE

Quality Gate FALSE:
  → Review Failure Reply
  → Reply to LINE

If FALSE:
  → Unsupported Input Reply
  → Reply to LINE1
```

## 6. Stage Responsibilities

| Stage | Responsibility |
|---|---|
| Analyze Image | Extract the visible mathematics question from the submitted image. |
| Question Analyzer | Classify and structure the interpreted question. |
| Solver | Generate the mathematical solution. |
| Examiner | Produce examiner-inspired assessment guidance. |
| Moderator | Check consistency between interpretation, solution, and assessment output. |
| Moderator Check | Route PASS results forward or route FAIL results to the safe failure reply. |
| Quality Checker | Review correctness, completeness, notation, clarity, and response structure. |
| Quality Gate | Route ready-for-student output forward or route failed output to the safe failure reply. |
| Formatter1 | Assemble topic, difficulty, assessment objective, solution, and assessment guidance. |
| Reply to LINE | Deliver the normal response or review-failure response. |
| Unsupported Input Reply | Create a message requesting a clear mathematics-question image. |
| Reply to LINE1 | Deliver the unsupported-input message. |

## 7. Failure Behavior

### Unsupported input

If the first IF node determines that the message is not a supported image input:

```text
If (false) → Unsupported Input Reply → Reply to LINE1
```

### Failed review

If either review gate rejects the generated work:

```text
Moderator Check (false) → Review Failure Reply → Reply to LINE
Quality Gate (false)    → Review Failure Reply → Reply to LINE
```

The current fallback message informs the user that the solution could not be safely verified and asks for a clearer question or teacher review.

These safeguards do not cover every possible runtime, API, network, or malformed-response failure. Production-grade retry, monitoring, and observability remain future work.

## 8. Diagram and Visual-Output Boundary

The current cloud MVP can process questions that contain diagrams or graphical information when the input can be interpreted successfully.

The current limitation is narrower than “no diagram support”:

- Diagram/graph **input** can be processed.
- Mathematical solutions for such questions can be generated.
- If the **final answer itself must be drawn or rendered visually**, the stable MVP currently returns text-based drawing instructions rather than a generated final image.
- Rendered visual-answer generation remains under active development.

The frozen 51-case baseline contains older visual/diagram metrics and remains unchanged as historical validation evidence.

## 9. Student-Facing Output

Normal output contains:

- Topic
- Difficulty
- Assessment Objective
- Step-by-step solution
- Final answer
- Examiner-inspired assessment guidance

Generated assessment guidance must not be described as an official Cambridge mark scheme or certified grade.

## 10. Quality Requirements

Every material workflow change should be checked for:

1. Input integrity
2. Curriculum fit
3. Mathematical validity
4. Assessment consistency
5. Output quality
6. Failure-route behavior
7. LINE delivery

Automated review is a safeguard, not proof of correctness.

## 11. Security and Privacy

Public artifacts must not contain:

- OpenAI API keys
- LINE access tokens or channel secrets
- n8n credential IDs
- private webhook identifiers where sensitive
- instance IDs
- raw reply tokens
- LINE user identifiers
- private student submissions

The public workflow must remain sanitized and inactive.

## 12. Validation Boundary

The 51-case validation record is a frozen baseline. Later cloud deployment and workflow-routing changes do not automatically update those metrics.

New metrics require a new versioned evaluation rather than silent replacement of the historical baseline.

## 13. Roadmap Priorities

### Active

- Improve diagram/graph interpretation.
- Develop rendered visual-answer generation.
- Extend regression testing.
- Improve monitoring and operational reliability.

### Planned

- Persistent data services.
- Teacher dashboard.
- PDF delivery.
- Analytics.
- Additional curricula.
- Multilingual support.
- Institution-level administration and access controls.

## 14. Source of Truth

For current product status, use:

1. `SPEC.md`
2. `README.md`
3. `docs/deployment-status.md`
4. `workflow/README.md`
5. `docs/system-architecture.md`
6. `docs/ai-workflow.md`

Historical reports and frozen validation records should not be silently rewritten to reflect later deployment changes.
