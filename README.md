# Project Scaffold

Template repository with pre-configured CI (Python tests, semantic-release),
Issue/PR templates, and commit convention enforcement.

## What's included

| File | Description |
|---|---|
| `.github/workflows/ci.yml` | Python CI — multi-OS matrix, uv + pytest |
| `.github/workflows/release.yml` | Semantic release on `main` push |
| `.github/workflows/pr-template-check.yml` | Enforces PR body matches template |
| `.github/workflows/issue-validator.yml` | Validates issue form submissions |
| `.github/workflows/deploy-docs.yml` | MkDocs deployment (optional) |
| `.github/ISSUE_TEMPLATE/` | Bug report + Feature request forms |
| `.github/pull_request_template.md` | Structured PR template |
| `.github/COMMIT_CONVENTION.md` | Commit convention reference |
| `commitlint.config.js` | Conventional commits enforcement |
| `pyproject.toml` | Python project config (replace with your own) |
| `package.json` | Node config for commitlint + semantic-release |

## Secrets

| Secret | Required by | Notes |
|---|---|---|
| `GITHUB_TOKEN` | release.yml | Auto-provided |
| `DEEPSEEK_API_KEY` | (none by default) | Add if tests need LLM |
| `BRAVE_API_KEY` | (none by default) | Add if tests need web search |

## GitHub Action: Issue Validator

This repo includes `action.yml` — a reusable GitHub Action that:
- Validates bug report template completeness
- Runs AI-powered log authenticity review
- Auto-comments on incomplete or suspicious issues

```yaml
- uses: 14790897/project-scaffold@main
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    ai-api-key: ${{ secrets.DEEPSEEK_API_KEY }}
```
