# AGENTS.md

Instructions for AI coding agents working in the Math Intellect repository.

## Mission

Help develop and document Math Intellect without overstating what the functional
MVP currently does. Protect credentials and learner data, preserve mathematical
and evidentiary accuracy, and keep implemented capabilities clearly separated
from planned work.

Read [SPEC.md](SPEC.md), [README.md](README.md), [SECURITY.md](SECURITY.md), and
[workflow/README.md](workflow/README.md) before making material changes.

## Repository Character

This is currently a documentation- and workflow-centered repository, not a
conventional application source tree. The executable artifact is a sanitized,
inactive n8n JSON export. Reports, samples, diagrams, screenshots, and validation
records are evidence artifacts. Do not invent build commands, test suites,
deployments, databases, APIs, or product features that do not exist.

## Working Rules

1. Inspect the relevant files and current Git diff before editing.
2. Make the smallest coherent change that satisfies the task.
3. Preserve user-authored work and unrelated changes.
4. Prefer Markdown source over editing generated PDF, PPTX, or image artifacts.
5. Keep public documentation understandable to educators and technical reviewers.
6. Use relative repository links and verify that referenced paths exist.
7. Do not change published metrics without checking the validation workbook and
   its documented denominator and applicability rules.
8. Do not describe roadmap items as implemented, validated, deployed, adopted,
   partnered, or commercially proven.
9. Record important assumptions and unresolved discrepancies in the handoff.

## Required Domain Guardrails

- A correct-looking solution to an incorrectly interpreted question is a failure.
- Moderator and Quality Checker outputs are automated review, not proof.
- Examiner output is examiner-inspired guidance, not an official Cambridge mark
  scheme, grade, or certification.
- Math Intellect is independent and is not affiliated with or endorsed by
  Cambridge University Press & Assessment.
- `0580` support in the workflow must not be generalized into demonstrated
  end-to-end `0606` coverage.
- Locally hosted n8n plus ngrok is development infrastructure, not production
  cloud hosting.
- The reported visual/diagram interpretation baseline is a known serious
  limitation; do not obscure it with a higher downstream metric.

## Security and Privacy

Never read, print, commit, or copy secrets into prompts, patches, logs, screenshots,
examples, or documentation. Prohibited public content includes:

- API keys, access tokens, channel secrets, credential IDs, and live webhook IDs;
- `.env` files or private n8n exports;
- raw LINE events, reply tokens, user IDs, and student identifiers;
- identifiable student submissions or private educational records.

Use placeholders matching [.env.example](.env.example). Treat suspicious strings
as potentially live credentials. Stop and alert the owner if one is found; do not
repeat it in chat or commit messages. Sanitization does not revoke a credential.

Use self-authored or appropriately licensed sample questions. Avoid publishing
copyrighted examination papers or mark schemes beyond permitted quotation or
reference use.

## Workflow Editing

The public workflow is
`workflow/math-intellect-workflow-sanitized.json`.

- Treat it as an inspection artifact, not the production workflow.
- Keep `active` set to `false` in public exports.
- Do not add credential objects, instance IDs, original webhook paths, pinned
  execution data, or live tokens.
- Preserve valid n8n structure, node types, node versions, expressions, and
  connections unless the requested change requires them to change.
- Inspect both outputs of IF/gate nodes. A happy-path connection is not sufficient
  evidence of safe failure behavior.
- If a node name changes, update every expression, connection, and document that
  references it.
- Test imports only in a separate development n8n instance; never overwrite a
  functioning private workflow.
- Do not claim successful execution unless it was actually run and the tested
  path, inputs, and result are documented.

## Documentation Consistency

For changes to architecture, stages, features, status, metrics, or roadmap, search
for all related claims before editing. Commonly affected files include:

- `README.md`
- `SPEC.md`
- `workflow/README.md`
- `docs/system-architecture.md`
- `docs/ai-workflow.md`
- `docs/quality-assurance.md`
- `docs/validation-methodology.md`
- `docs/roadmap.md`
- sample READMEs and captions

Use these status labels consistently: **implemented**, **development only**,
**planned**, **reported**, and **not independently verified**. Prefer precise
language over promotional wording.

## Validation

There is no repository-wide automated test suite at present. Use the checks that
fit the changed files.

### Baseline repository checks

```bash
git diff --check
jq empty workflow/math-intellect-workflow-sanitized.json
rg -n "(OPENAI_API_KEY|LINE_CHANNEL_ACCESS_TOKEN|LINE_CHANNEL_SECRET)=" . \
  --glob '!*.pdf' --glob '!*.pptx' --glob '!*.xlsx'
```

The secret search should return only safe placeholders, if any. Also inspect the
diff manually for tokens, personal data, unsupported claims, broken relative
links, and accidental binary changes.

### Workflow changes

- Confirm the node count and names intentionally changed.
- Inspect connections and both success/failure branches.
- Import into a separate test instance and reconnect test credentials through
  n8n's credential system.
- Exercise at least one expected-success case and each changed failure path.
- Independently verify mathematical output and inspect the final LINE message.

### Validation-document changes

- Trace each figure to the workbook/source record.
- Preserve denominators, N/A handling, rounding, and metric scope.
- Never silently replace the frozen 51-case baseline; version new studies.

## Definition of Done

A task is complete only when the requested files are changed, relevant checks
pass, security/privacy review is complete, related documentation remains
consistent, and the handoff accurately states what was and was not tested.

Do not push, publish, deploy, activate a workflow, rotate credentials, or contact
external users unless the owner explicitly asks for that action.
