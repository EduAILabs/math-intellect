# CLAUDE.md

Claude-specific guidance for working on Math Intellect.

Follow `AGENTS.md` and `SPEC.md`.

## Start Here

Before editing, read:

1. `SPEC.md`
2. `README.md`
3. `AGENTS.md`
4. `SECURITY.md`
5. `docs/deployment-status.md`
6. `workflow/README.md`
7. task-relevant files under `docs/`

## Current Project State

Math Intellect is a LINE-based, n8n-orchestrated **cloud-deployed functional MVP**.

```text
LINE image
→ n8n Cloud webhook
→ input check
→ image retrieval
→ Analyze Image
→ Question Analyzer
→ Solver
→ Examiner
→ Moderator
→ Moderator Check
→ Quality Checker
→ Quality Gate
→ Formatter
→ LINE response
```

Failure routes are also implemented:

```text
Unsupported input
→ Unsupported Input Reply
→ Reply to LINE1

Moderator Check false
→ Review Failure Reply
→ Reply to LINE

Quality Gate false
→ Review Failure Reply
→ Reply to LINE
```

The public GitHub workflow is sanitized and inactive. The live n8n Cloud editor is private.

## Non-Negotiable Constraints

- Never expose secrets or private workflow credentials.
- Never hard-code live LINE/OpenAI authorization values into public files.
- Keep the public JSON inactive.
- Never call examiner-inspired guidance an official mark scheme or grade.
- Never claim Cambridge affiliation.
- Never present a quality-gate pass as proof of correctness.
- Preserve the frozen 51-case baseline as historical validation evidence.
- Do not claim a new aggregate validation rate unless a new controlled evaluation exists.
- Do not describe the current live MVP as production SaaS or institution-ready.
- Do not describe rendered visual-answer generation as complete.

## Diagram / Visual Boundary

The current live MVP may process diagram-containing or graphical input questions.

If the final answer itself requires a rendered diagram, graph, construction, transformation, or other visual, the stable MVP currently returns text-based drawing instructions. Visual rendering remains under active development.

## Documentation Review

When changing deployment, routing, or capability claims, check all related Markdown files. Avoid leaving “local-only”, “cloud planned”, or “no failure reply” claims after those states have changed.

## Validation Claims

Use `docs/validation-methodology.md` as the scope guardrail.

The frozen validation baseline predates some later workflow and cloud-deployment changes. Treat later successful tests as current evidence, not as a replacement aggregate benchmark.

## Handoff

At completion, state:

1. files changed;
2. current behavior documented;
3. checks performed;
4. what remains unverified; and
5. any open security, mathematical, or documentation risk.

Do not push or publish without explicit owner authorization.
