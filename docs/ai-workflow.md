# AI Workflow

## Math Intellect — Current Cloud MVP

**Project Lead:** Ngwe Htoon (Howard)  
**Document status:** Current implemented workflow behavior.

## Purpose

Math Intellect uses a sequential n8n Cloud workflow to convert a mathematics-question image submitted through LINE into a structured text response.

The workflow separates intake, image interpretation, question analysis, solving, assessment review, moderation, quality checking, formatting, and delivery.

## End-to-End Flow

```text
LINE image
→ Webhook
→ Edit Fields
→ If
→ Download Image
→ Analyze Image
→ Edit Fields1
→ Question Analyzer
→ Solver
→ Examiner
→ Moderator
→ Moderator Check
→ Quality Checker
→ Quality Gate
→ Formatter1
→ Reply to LINE
```

## Processing Stages

| Stage | Responsibility |
|---|---|
| Analyze Image | Extract the visible mathematics question. |
| Question Analyzer | Identify topic, subtopic, difficulty, and assessment objective. |
| Solver | Generate the mathematical solution. |
| Examiner | Produce examiner-inspired assessment guidance. |
| Moderator | Check mathematical consistency. |
| Quality Checker | Review notation, completeness, clarity, and assessment format. |
| Formatter1 | Assemble the student-facing response. |

## Input Routing

The first IF node distinguishes supported image input from unsupported input.

### Supported image

```text
If (true) → Download Image → ...
```

### Unsupported input

```text
If (false)
→ Unsupported Input Reply
→ Reply to LINE1
```

This gives the user a direct request to send a clear image of a mathematics question.

## Review Routing

### Moderator Check

```text
Moderator Check (true)
→ Quality Checker

Moderator Check (false)
→ Review Failure Reply
→ Reply to LINE
```

### Quality Gate

```text
Quality Gate (true)
→ Formatter1
→ Reply to LINE

Quality Gate (false)
→ Review Failure Reply
→ Reply to LINE
```

The review-failure route prevents the normal formatted answer from being sent when the current review gates reject the result.

## Student-Facing Response

Normal output contains:

- Topic
- Difficulty
- Assessment Objective
- Solution
- Final answer
- Examiner-inspired assessment guidance

Generated assessment guidance is not an official examination mark scheme.

## Diagram and Graphical Questions

The current cloud MVP can process input questions containing diagrams or graphs when the information is successfully interpreted.

If the required **final response itself must be rendered visually**, the current stable workflow returns text-based drawing instructions rather than a generated image. Rendered visual output remains under active development.

## Current Deployment

The stable reviewer-facing workflow is deployed on n8n Cloud.

The live n8n workspace is private. The public repository contains a sanitized inactive JSON export for technical inspection.

## Known Boundaries

- Image clarity affects interpretation quality.
- AI stages can still produce mathematical or interpretive errors.
- Review gates are safeguards, not independent proof.
- Runtime/API/network failures are not yet covered by production-grade retry and monitoring.
- Persistent learner records, teacher dashboards, institutional controls, and production SaaS operations remain future work.
- Frozen validation metrics must not be treated as automatically updated by later cloud deployment changes.

## Related Documents

- [Deployment status](deployment-status.md)
- [System architecture](system-architecture.md)
- [Quality assurance](quality-assurance.md)
- [Validation methodology](validation-methodology.md)
- [Workflow export notes](../workflow/README.md)
