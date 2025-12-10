# How to Use Continuous Actions 📖

This guide explains how to integrate Continuous Actions templates into your GitHub workflows.

## 🚀 Quick Start

All actions in this repository are **composite actions** that can be referenced directly in your GitHub workflows. They are located in the `templates/` directory.

## 📋 Basic Usage

To use any action from this repository, add it to your workflow file (`.github/workflows/*.yml`) using the following syntax:

```yaml
- name: Step Name
  uses: JhonesBomfim/Continuos-Actions/templates/<action-name>@<branch-or-tag>
```

### Example Workflow

Here's a complete example of a workflow using multiple actions:

```yaml
name: CI Pipeline

on:
  pull_request:
    branches: [main, develop]
  push:
    branches: [main, develop]

jobs:
  quality-checks:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Run Linting
        uses: JhonesBomfim/Continuos-Actions/templates/lint@main

      - name: Run Security Scan
        uses: JhonesBomfim/Continuos-Actions/templates/security_scan@main

      - name: Check Documentation
        uses: JhonesBomfim/Continuos-Actions/templates/check_docs@main
```

## 📦 Available Actions

### 1. Linting

Validates code quality using pre-commit hooks.

```yaml
- name: Run Linting
  uses: JhonesBomfim/Continuos-Actions/templates/lint@main
```

**Requirements:**

- Python project with `pyproject.toml`
- Pre-commit configuration file (`.pre-commit-config.yaml`)

---

### 2. Security Scan

Analyzes dependencies for known vulnerabilities using pip-audit.

```yaml
- name: Security Scan
  uses: JhonesBomfim/Continuos-Actions/templates/security_scan@main
```

**Requirements:**

- Python project with dependencies

---

### 3. Check Conflicts

Detects merge conflicts before merging pull requests.

```yaml
- name: Check for Merge Conflicts
  uses: JhonesBomfim/Continuos-Actions/templates/check_conflicts@main
```

**Best used on:** Pull request events

---

### 4. Check Merge

Verifies if there are conflict markers in the code.

```yaml
- name: Check Merge Markers
  uses: JhonesBomfim/Continuos-Actions/templates/check_merge@main
```

---

### 5. Check Draft

Validates if pull request is still in draft mode.

```yaml
- name: Check Draft Status
  uses: JhonesBomfim/Continuos-Actions/templates/check_draft@main
```

**Best used on:** Pull request events

---

### 6. Check Docs

Ensures documentation files exist and are valid.

```yaml
- name: Validate Documentation
  uses: JhonesBomfim/Continuos-Actions/templates/check_docs@main
```

**Validates:**

- `README.md` exists and has minimum 3 lines
- `LICENSE` file exists
- No broken links in README

---

### 7. Tag Release

Automatically creates tags and GitHub releases based on `.version` file.

```yaml
- name: Create Release
  uses: JhonesBomfim/Continuos-Actions/templates/tag_release@main
  env:
    GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

**Requirements:**

- `.version` file in repository root
- GitHub CLI (`gh`) access

---

### 8. Template Validate

Validates project structure and required files.

```yaml
- name: Validate Project Template
  uses: JhonesBomfim/Continuos-Actions/templates/template_validate@main
```

**Validates:**

- Required files: `pyproject.toml`, `README.md`, `LICENSE`, `.gitignore`, `.pre-commit-config.yaml`
- Valid `pyproject.toml` structure
- GitHub Actions directory structure

---

## 🎯 Recommended Workflows

### For Pull Requests

```yaml
name: PR Checks

on:
  pull_request:
    branches: [main, develop]

jobs:
  validation:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Check Draft
        uses: JhonesBomfim/Continuos-Actions/templates/check_draft@main

      - name: Check Conflicts
        uses: JhonesBomfim/Continuos-Actions/templates/check_conflicts@main

      - name: Check Merge Markers
        uses: JhonesBomfim/Continuos-Actions/templates/check_merge@main

      - name: Lint Code
        uses: JhonesBomfim/Continuos-Actions/templates/lint@main

      - name: Security Scan
        uses: JhonesBomfim/Continuos-Actions/templates/security_scan@main
```

### For Releases

```yaml
name: Release

on:
  push:
    branches: [main]

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Validate Template
        uses: JhonesBomfim/Continuos-Actions/templates/template_validate@main

      - name: Check Documentation
        uses: JhonesBomfim/Continuos-Actions/templates/check_docs@main

      - name: Create Release
        uses: JhonesBomfim/Continuos-Actions/templates/tag_release@main
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

---

## 💡 Tips

1. **Use specific versions:** Instead of `@main`, use `@v1.0.0` for production workflows
2. **Checkout required:** Always use `actions/checkout@v4` before any action
3. **Permissions:** Some actions may require specific GitHub token permissions
4. **Combine actions:** Most actions can be used together in the same workflow

---

## 🔗 Links

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Composite Actions Guide](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action)

---

**Need help?** Open an issue in the [repository](https://github.com/JhonesBomfim/Continuos-Actions).
