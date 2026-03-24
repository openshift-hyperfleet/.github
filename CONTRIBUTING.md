# Contributing to HyperFleet

Thank you for your interest in contributing to HyperFleet! This guide covers the conventions and workflow shared across all HyperFleet repositories.

## Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/<repo>.git
   cd <repo>
   ```
3. **Add the upstream remote**:
   ```bash
   git remote add upstream https://github.com/openshift-hyperfleet/<repo>.git
   ```

## Development Setup

### Prerequisites

- Go (see `go.mod` in each repo for the required version)
- Docker (for building images)
- `make` (for running Makefile targets)
- Helm 3 (for chart development)

### Common Make Targets

All HyperFleet repositories share a standard set of Make targets:

| Target | Description |
|--------|-------------|
| `make build` | Build the binary |
| `make test` | Run unit tests |
| `make test-all` | Run all tests (unit + integration + lint + helm) |
| `make lint` | Run golangci-lint |
| `make fmt` | Format code |
| `make tidy` | Run go mod tidy |
| `make test-helm` | Validate Helm chart templates |

## Branch and Commit Conventions

### Branch Naming

Name branches after the Jira ticket:

```
HYPERFLEET-123
```

### Commit Messages

Follow this format:

```
HYPERFLEET-<ID> - <type>: <description>
```

**Types:**
- `feat` — New feature
- `fix` — Bug fix
- `chore` — Maintenance, dependencies, CI
- `test` — Adding or updating tests
- `docs` — Documentation changes
- `refactor` — Code restructuring without behavior change

**Examples:**
```
HYPERFLEET-789 - feat: add OpenTelemetry span exporter to adapter
HYPERFLEET-630 - fix: consolidate duplicate resource operation logs
HYPERFLEET-786 - chore: align chart with Helm conventions standard
HYPERFLEET-733 - test: add precedence test for overlapping decision checks
```

## Pull Request Process

1. **Rebase on latest main** before submitting:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

2. **Run all checks**:
   ```bash
   make test-all
   ```

3. **Push and create a PR**:
   ```bash
   git push origin HYPERFLEET-<ID>
   ```

4. **PR requirements**:
   - Clear title matching commit convention: `HYPERFLEET-<ID> - <type>: <description>`
   - Summary of changes and test plan in the description
   - All CI checks passing
   - At least one approval before merging

## Testing Beyond Unit Tests

For Helm chart or configuration changes, deploy to a development cluster and verify the changes work end-to-end. Use [hyperfleet-infra](https://github.com/openshift-hyperfleet/hyperfleet-infra) to provision your own cluster.

For cross-component or major changes, run the E2E test suite from [hyperfleet-e2e](https://github.com/openshift-hyperfleet/hyperfleet-e2e) against your development cluster before submitting.

## Code Style

- Follow [Effective Go](https://go.dev/doc/effective_go) guidelines
- Run `make fmt` and `make lint` before committing
- Write table-driven tests when testing multiple scenarios
- Handle errors explicitly — don't ignore them
- Add comments for exported functions, types, and packages

## Issue Tracking

HyperFleet uses [Jira](https://redhat.atlassian.net/jira/software/projects/HYPERFLEET/boards/1013) for issue tracking. GitHub Issues are available for external contributors, but team members should use Jira.

## Questions?

If you have questions or need help:

1. Check existing issues and pull requests
2. Open a new issue with the `question` label
3. Reach out to the HyperFleet team at **openshift-hyperfleet@redhat.com** or on Slack channel **#hcm-hyperfleet-team** (Red Hat workspace)
