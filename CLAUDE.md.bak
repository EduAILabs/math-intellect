# CLAUDE.md

Claude-specific guidance for working on Math Intellect. Follow the repository-wide
instructions in [AGENTS.md](AGENTS.md) and the product contract in
[SPEC.md](SPEC.md); this file adds a concise operating workflow for Claude Code.

## Start Here

Before editing, read:

1. `SPEC.md`
2. `README.md`
3. `AGENTS.md`
4. `SECURITY.md`
5. `workflow/README.md`
6. the task-relevant file under `docs/`

Then inspect `git status --short`, the current diff, and all references to the
term, metric, node, or feature you plan to change.

## Project Model

Math Intellect is a LINE-based, n8n-orchestrated functional MVP. Its current
application flow is:

```text
LINE image → intake and image retrieval → Analyze Image → Question Analyzer
→ Solver → Examiner → Moderator → Quality Checker → JavaScript Formatter
→ LINE text response
```

The repository contains a sanitized public workflow and supporting documentation
and evidence. It does not contain a production deployment or a conventional
application build/test toolchain.

## How to Work

- Plan only as much as needed; keep edits narrow and reviewable.
- Do not infer product status from aspirational documents. Confirm it in the
  current-system and workflow documentation.
- Search before changing shared terminology or status claims.
- Edit source Markdown or JSON rather than generated reports and screenshots.
- Explain uncertainty instead of filling gaps with plausible details.
- Keep educational, technical, and evidence claims distinct.
- Never push, deploy, activate the workflow, or modify external services without
  explicit authorization.

## Non-Negotiable Constraints

- Never expose or commit secrets, private exports, raw LINE payloads, student
  data, or identifiable submissions.
- Never hard-code LINE or OpenAI authorization values in workflow JSON.
- Keep the public n8n workflow inactive and sanitized.
- Never call examiner-inspired guidance an official mark scheme or grade.
- Never claim Cambridge affiliation or endorsement.
- Never present a quality-gate pass as proof of correctness.
- Never generalize the 95.65% final-answer figure to arbitrary submitted images;
  consult `docs/validation-methodology.md` for metric scope.
- Never conceal the 4.17% visual/diagram interpretation limitation.
- Never describe planned cloud, dashboard, database, PDF, analytics, multilingual,
  or institutional features as current.

If a requested change conflicts with these constraints, stop and explain the
conflict rather than silently weakening the safeguard.

## Useful Inspection Commands

```bash
rg --files
rg -n "search term" README.md SPEC.md AGENTS.md CLAUDE.md docs workflow samples
jq '{name, active, node_count:(.nodes|length), nodes:[.nodes[].name]}' \
  workflow/math-intellect-workflow-sanitized.json
jq '.connections' workflow/math-intellect-workflow-sanitized.json
git diff --check
git diff --stat
git diff
```

For a final credential check, use the safe procedure in `AGENTS.md`. Do not print
suspected secret values; report the file and remediation need without echoing the
credential.

## Task-Specific Review

### Documentation

Verify relative links, consistent terminology, implemented/planned boundaries,
and claims against the narrowest source of truth listed in `SPEC.md`.

### n8n workflow JSON

Validate JSON, inspect node references and all gate branches, keep `active: false`,
and ensure credentials and instance identifiers remain absent. Imported execution
must occur only in a separate development instance with test credentials.

### Prompts or mathematical behavior

Check the complete chain: source-image fidelity, question reconstruction, method,
working, final answer, assessment guidance, moderation, and rendered output. Use
independent mathematical verification. Internal agreement among AI stages is not
enough.

### Validation claims

Use the workbook/evidence as the source of record. Preserve metric denominators,
applicability rules, N/A treatment, rounding, and the frozen baseline. Version a
new evaluation rather than overwriting old results.

## Handoff Format

At completion, state:

1. what changed;
2. which checks were run and their results;
3. what was not run or independently verified;
4. any security, privacy, mathematical, or documentation risk still open; and
5. the exact files requiring owner review.

Be precise and restrained. The goal is a trustworthy educational system and an
auditable public record, not the strongest possible marketing claim.
