# .github

Organization-wide default [community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) and templates for all [openshift-hyperfleet](https://github.com/openshift-hyperfleet) repositories.

GitHub automatically applies these defaults to any repository in the organization that does not define its own version.

## What's Included

| File | Purpose |
|------|---------|
| `PULL_REQUEST_TEMPLATE.md` | Standard PR template with summary, test plan, and checklist |
| `ISSUE_TEMPLATE/bug_report.yml` | Bug report form with component dropdown and severity |
| `ISSUE_TEMPLATE/feature_request.yml` | Feature request form with component dropdown |
| `ISSUE_TEMPLATE/config.yml` | Issue chooser with Jira link for team members |
| `CONTRIBUTING.md` | Development setup, commit conventions, and PR workflow |
| `CODE_OF_CONDUCT.md` | Community code of conduct |
| `SECURITY.md` | Vulnerability reporting process |

## How It Works

- Files in this repo serve as **defaults** for all repos under `openshift-hyperfleet`
- If a repo defines its own version (e.g., its own `PULL_REQUEST_TEMPLATE.md`), the repo-level file takes precedence
- Changes here propagate automatically to all repos that rely on the defaults

## Contributing

To propose changes to org-wide templates, open a PR against this repository. Changes affect all HyperFleet repositories that don't override the template locally.
