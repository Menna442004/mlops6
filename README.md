# CI/CD Gatekeeper Pipeline
This project implements a CI/CD pipeline using GitHub Actions with a gatekeeper logic to prevent unnecessary GPU usage.

## Jobs

### 1. Linter Job
- Runs first
- Checks code quality
- Must pass before training

### 2. Train Job (Expensive)
Runs ONLY if:
- Linter passes
- Branch is `main`
- Commit message contains `[run-train]`

## Features
- Skips training when conditions are not met
- Uploads `error_logs.txt` if training fails
- Performs cleanup using `always()`