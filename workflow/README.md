# Math Intellect — Public Workflow Export

## AI-Assisted Mathematics Learning Platform

**Project Lead:** Ngwe Htoon (Howard)  
**Document status:** Sanitized public technical copy of the current 18-node MVP workflow logic.

## Purpose

This folder contains a sanitized n8n workflow export for technical inspection.

The public file preserves the current node structure and routing logic while removing credentials, live tokens, live instance identifiers, and private deployment metadata.

The public JSON is **inactive**. It is not the live n8n Cloud workspace.

## Current Workflow Structure

The current workflow contains 18 nodes.

### Supported-image path

```text
Webhook
→ Edit Fields
→ If
→ Download Image
→ Analyze Image
→ Edit Fields1 (Filter Out To Get Only Q Data)
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

### Unsupported-input path

```text
Edit Fields
→ If (false)
→ Unsupported Input Reply
→ Reply to LINE1
```

### Moderator failure path

```text
Moderator
→ Moderator Check (false)
→ Review Failure Reply
→ Reply to LINE
```

### Quality failure path

```text
Quality Checker
→ Quality Gate (false)
→ Review Failure Reply
→ Reply to LINE
```

## Node Roles

| Node | Role |
|---|---|
| Webhook | Receive LINE event |
| Edit Fields | Normalize required event fields |
| If | Check supported image input |
| Download Image | Retrieve LINE image |
| Analyze Image | Extract question content |
| Edit Fields1 | Normalize extracted question data |
| Question Analyzer | Classify question context |
| Solver | Generate solution |
| Examiner | Generate examiner-inspired guidance |
| Moderator | Consistency review |
| Moderator Check | PASS/FAIL routing |
| Quality Checker | Additional quality review |
| Quality Gate | Ready-for-student routing |
| Formatter1 | Assemble final normal response |
| Reply to LINE | Deliver normal or review-failure reply |
| Unsupported Input Reply | Build unsupported-input feedback |
| Reply to LINE1 | Deliver unsupported-input feedback |
| Review Failure Reply | Build safe review-failure feedback |

## Current Live Deployment vs Public Export

### Live system

- deployed on n8n Cloud;
- connected to the Math Intellect LINE Official Account;
- uses private credentials;
- active for reviewer-facing testing.

### Public GitHub export

- sanitized;
- inactive;
- credentials removed;
- live workflow/instance IDs removed;
- safe for technical inspection after secret review;
- requires credential configuration after import.

## Import Notes

After importing into a separate test n8n instance:

1. configure OpenAI credentials for all OpenAI nodes;
2. configure a LINE HTTP Bearer credential for image retrieval and reply nodes;
3. set a test webhook path;
4. connect the LINE test channel;
5. test the supported-input path;
6. test unsupported input;
7. test Moderator Check failure;
8. test Quality Gate failure;
9. verify normal and fallback LINE messages.

Do not use the public JSON as a drop-in production deployment.

## Diagram / Visual Boundary

The workflow may process diagram-containing questions when the input is interpreted successfully.

If the final answer requires a rendered visual, the stable reviewer-facing MVP currently returns text-based drawing instructions. Rendered image output remains under development.

## Security

Never publish:

- API keys;
- LINE channel access tokens;
- LINE channel secrets;
- credential IDs;
- instance IDs;
- raw reply tokens;
- user IDs;
- private student content.

If a live credential was ever exposed in another export, removing it from this file does not revoke it. Rotate exposed credentials separately.

## Validation Boundary

The 51-case validation record is a frozen baseline. The current cloud deployment and later routing updates do not automatically update those metrics.

## Related Documentation

- [Root README](../README.md)
- [Current deployment status](../docs/deployment-status.md)
- [System architecture](../docs/system-architecture.md)
- [AI workflow](../docs/ai-workflow.md)
- [Quality assurance](../docs/quality-assurance.md)
- [Validation methodology](../docs/validation-methodology.md)
