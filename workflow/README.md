# Math Intellect — Workflow Export

## AI-Assisted Mathematics Learning Platform

**Project Lead:** Ngwe Htoon (Howard)  
**Document status:** Sanitized public copy of the supplied, reportedly successful MVP validation workflow. It documents implementation, but the sanitized copy has not been independently imported or executed.

## Overview

This folder contains a sanitized n8n workflow export of Math Intellect for technical inspection.

The export preserves the 15-node workflow, including its connections, AI processing stages model configurations, and JavaScript-based response formatting.

Credentials and instance-specific identifiers have been removed or replaced for public sharing. The workflow is inactive and export for technical inspection; requires credentials and environment configuration before use.

This export documents the functional MVP architecture. It is not a production-ready deployment.

```text
LINE image → Webhook → Edit Fields → If (image check)
→ Download Image → Analyze Image → Edit Fields1 → Question Analyzer
→ Solver → Examiner → Moderator → Moderator Check
→ Quality Checker → Quality Gate → Formatter1 → Reply to LINE
```

The six *application stages* in the [root README](../README.md) are Question Analyzer → Solver → Examiner → Moderator → Quality Checker → Formatter. Other nodes perform image intake, routing and delivery; `Formatter1` is the actual JavaScript node implementing the Formatter stage.

## File

- [math-intellect-workflow-sanitized.json](math-intellect-workflow-sanitized.json) — sanitized n8n export.

## Changes Made for Public Sharing

| Original export content | Treatment in this public copy |
|---|---|
| Hard-coded LINE channel access token in `Reply to LINE` | Removed the entire Authorization header; set this node to use an n8n HTTP Bearer credential configured separately after import. |
| n8n credential IDs and display names for OpenAI and the LINE image-download node | Removed all per-node `credentials` objects. |
| Original webhook ID and path | Removed original webhook ID; substituted `math-intellect-public-example` for the path. |
| n8n instance metadata, workflow ID and version ID | Removed. |
| Per-node UUIDs | Replaced with new UUIDs; node names and links were preserved. |
| Active state and pinned execution data | Set `active` to `false` and `pinData` to an empty object. |

**Security action required:** The original JSON contains a LINE channel access token in plaintext. Revoke or rotate that token in the appropriate LINE account before publishing any repository material. Removing it from this exported file does not invalidate the token. If the original JSON was ever committed, also remediate the secret in Git history; assume the exposed token is compromised. Do not upload the original export, student submissions, LINE user IDs, reply tokens or credentials.

The public file retains workflow logic and prompts, which may reveal implementation details. Review their suitability for public release before committing. The sanitization does not constitute an independent security audit of the n8n instance, API accounts or connected services.

## Import and Setup (Development Only)

1. Import the JSON into a **separate test n8n instance**. Do not overwrite the functioning private workflow.
2. In n8n, select a valid OpenAI credential for the six OpenAI nodes: `Analyze Image`, `Question Analyzer`, `Solver`, `Examiner`, `Moderator` and `Quality Checker`.
3. Create or select a secure n8n HTTP Bearer credential using a **new LINE channel access token** and attach it to both `Download Image` and `Reply to LINE`. Check the imported HTTP Request authentication settings in the UI; node-version differences may require reconfiguring the credential selection.
4. Set a unique webhook path/URL and point your LINE Messaging API webhook at that development endpoint. Keep all credentials out of source files and screenshots.
5. Test with a self-authored question and inspect the workflow outputs, IF branches, LINE reply and error paths before enabling any deployment. Recheck sharing permissions and remove personal data from screenshots.

This public export's JSON format and wiring have been checked. **No live import or end-to-end execution of the sanitized file has been performed here.** Reconnecting credentials is necessary; it is not a guarantee that an imported workflow will run without further adjustments.

## Confirmed Implementation Boundaries

- The original prompts target **Cambridge IGCSE Mathematics 0580** specifically. The broader project also references 0606, but this export is not evidence of end-to-end 0606 coverage.
- `Analyze Image` requests question-text extraction. The Solver's `DIAGRAM INFORMATION` expression references `$('Download Image').item.json.messageType`, **not extracted diagram geometry**. Instructions inside a prompt to consult the original image do not by themselves attach the image to the Solver. These original logic details have been preserved, not silently fixed, so the export reflects the workflow being documented.
- `Moderator Check` passes only `status == PASS`. Its false branch has no onward connection, so a `FAIL` does not reach the normal LINE answer path. `Quality Gate` similarly forwards only its true branch. See [Sample 02](../samples/sample-output-02.md) for an observed diagram-related failure with a moderator rejection.
- There is no user-facing retry response configured for rejected images or failed gate paths in the supplied export. This is a known limitation, not a claimed feature.
- Locally hosted n8n plus ngrok is development infrastructure. Production cloud hosting, a learner database, teacher dashboard, PDF delivery and institution-ready safeguards are not part of this public workflow.
- The Examiner creates **examiner-inspired** guidance, not official Cambridge marking or certified grades. An AI quality-gate pass is not independent proof of mathematical correctness.

## Related Documentation and Evidence

- [Root README](../README.md) — canonical project status and reported validation metrics.
- [System Architecture](../docs/system-architecture.md) and [AI Workflow](../docs/ai-workflow.md) — technical explanations.
- [Quality Assurance](../docs/quality-assurance.md) — five review dimensions and limitations.
- [Validation Methodology](../docs/validation-methodology.md) — interpretation of the reported 51-case baseline.
- [Sample Demonstrations](../samples/README.md) — selected success and failure cases.

The export is implementation/architecture evidence, not independent verification of the 51-case metrics, measured educational improvement, commercial traction, or production readiness. Math Intellect is independent and is not affiliated with or endorsed by Cambridge University Press & Assessment.
