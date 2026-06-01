# Rules Engine Workflow

This repository supports a Pentalym CODE conversion workflow for rule and policy changes.

## Workflow steps

1. Engineer opens the GitHub repository in VS Code.
2. Engineer installs or uses `@pentalym-code-conversion-agent`.
3. Engineer asks the agent to change a draft ruleset, for example: “Change suture length margin from 30% to 25% in draft ruleset.”
4. The agent identifies the correct YAML ruleset file.
5. The agent proposes the exact change.
6. Engineer commits the change to a branch.
7. A pull request is opened.
8. Docker validation runs in GitHub Actions via `.github/workflows/rules-validation.yml`.
9. The agent summarizes conversion impact, including match behavior and risk.
10. Reviewer approves or requests changes.
11. Merge publishes the new draft/published ruleset version.
12. Pentalym UI shows the new version, test result, and approval history.

## Repository components

- `Dockerfile` - container build for validation and regression tests.
- `package.json` - npm scripts for rule validation and conversion tests.
- `.github/workflows/rules-validation.yml` - GitHub Actions workflow.
- `.github/agents/pentalym-code-conversion.agent.md` - CODE conversion agent guidance.

## Notes

- The validation workflow currently runs on pull requests for `rules/**`, `inventory/**`, and `scripts/**`.
- The agent should be able to propose changes to draft rulesets and explain the downstream impact.
- New ruleset versions should be recorded in the YAML policy or ruleset metadata.
