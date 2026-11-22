# AGENTS.md

Instructions for AI coding agents working in the Math Intellect repository.

## Mission

Help develop and document Math Intellect accurately. Preserve the distinction between:

- the **live cloud-deployed functional MVP**,
- the **sanitized public workflow export**,
- the **local development environment for experimental features**, and
- future production SaaS / institutional capabilities.

Read `SPEC.md`, `README.md`, `SECURITY.md`, `docs/deployment-status.md`, and `workflow/README.md` before material changes.

## Current Project Model

Math Intellect currently has:

- a stable reviewer-facing MVP deployed on n8n Cloud;
- a live LINE Official Account as the public testing interface;
- a public GitHub repository containing sanitized technical evidence;
- a separate local development path for experimental visual-answer rendering and other unfinished features.

Do not describe the current live MVP as a production SaaS or institution-ready service.

## Required Guardrails

- A correct-looking solution to a misinterpreted question is a failure.
- Moderator and Quality Checker outputs are safeguards, not proof.
- Examiner output is examiner-inspired guidance, not an official Cambridge mark scheme.
- Math Intellect is independent and is not affiliated with or endorsed by Cambridge University Press & Assessment.
- The frozen 51-case validation baseline must not be silently replaced by later observations.
- Current diagram-containing inputs may be processed, but rendered visual-answer output remains under development.
- Do not generalize selected successful tests into universal reliability claims.

## Current Workflow Routing

The public sanitized workflow should reflect the current routing logic:

```text
If true
? Download Image
? Analyze Image
? Question Analyzer
? Solver
? Examiner
? Moderator
? Moderator Check

Moderator Check true ? Quality Checker
Moderator Check false ? Review Failure Reply ? Reply to LINE

Quality Gate true ? Formatter1 ? Reply to LINE
Quality Gate false ? Review Failure Reply ? Reply to LINE

If false ? Unsupported Input Reply ? Reply to LINE1
```

If node names or routing change, update all documentation that references them.

## Security and Privacy

Never commit or reproduce:

- API keys
- LINE access tokens or channel secrets
- n8n credential IDs
- instance IDs
- raw reply tokens
- identifiable user/student data
- private n8n exports

The public workflow export must be sanitized and inactive.

## Documentation Consistency

Architecture/status changes commonly affect:

- `README.md`
- `SPEC.md`
- `AGENTS.md`
- `CLAUDE.md`
- `workflow/README.md`
- `docs/deployment-status.md`
- `docs/system-architecture.md`
- `docs/ai-workflow.md`
- `docs/quality-assurance.md`
- `docs/roadmap.md`
- `docs/commercialization-plan.md`
- `docs/market-analysis.md`
- `docs/educational-impact.md`
- `docs/validation-methodology.md`

Use these labels consistently:

- **implemented**
- **live MVP**
- **development only**
- **planned**
- **frozen validation baseline**
- **not independently verified**

## Workflow Review

For workflow changes:

- inspect both true and false branches;
- validate the unsupported-input route;
- validate Moderator Check failure routing;
- validate Quality Gate failure routing;
- verify normal LINE response delivery;
- verify safe fallback reply delivery;
- keep the public JSON free of credentials and active deployment identifiers.

## Definition of Done

A documentation or workflow task is complete only when:

1. changed behavior is accurately reflected across affected docs;
2. security/privacy checks are complete;
3. no historical validation metric is silently changed;
4. live MVP status is not confused with future production SaaS status; and
5. the owner can review exactly what changed before publication.

Do not push, publish, deploy, rotate credentials, or modify external services unless explicitly authorized.
