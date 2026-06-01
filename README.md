# pentalym-medtronic-rules-engine

A rules-engine repository for Pentalym / Medtronic CODE conversion workflows.

## Ruleset lifecycle

This repository supports the following end-to-end process:

1. Engineer edits a ruleset under `rules/` or related directories.
2. An open pull request triggers GitHub Actions.
3. The workflow builds a Docker validation container.
4. The container runs rule validation and conversion regression tests.
5. The Pentalym agent summarizes the ruleset change and match impact.
6. Reviewer sees pass/fail status and reviews the match behavior.
7. Approved change is merged.
8. The new ruleset version is recorded in the repository.

## Automation

- Workflow: `.github/workflows/rules-validation.yml`
- Dockerfile: `Dockerfile`
- Package manifest: `package.json`
- Agent definition: `.github/agents/pentalym-code-conversion.agent.md`
- Workflow documentation: `docs/rules-engine-workflow.md`

## NPM scripts

- `npm run validate:rules` — validate rulesets
- `npm run test:conversion` — run conversion regression tests
- `npm run explain:match` — generate match explanations
