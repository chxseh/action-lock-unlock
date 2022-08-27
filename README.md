# Lock/Unlock a PR/Issue

Based on [sudo-bot/action-pull-request-lock](https://github.com/sudo-bot/action-pull-request-lock)

## Example Usage

### Lock a PR/Issue
```yml
---
name: "🔒 Lock Resolved Issues/PRs"

on:
  pull_request:
    types:
      - closed
  issues:
    types:
      - closed

jobs:
  lock:
    runs-on: ubuntu-latest

    steps:
      - uses: chxseh/action-lock-unlock@v1.0.0
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          number: ${{ github.event.pull_request.number || github.event.issue.number }}
          lock: true
          lock-reason: resolved
```

### Unlock a PR/Issue
```yml
---
name: "🔓 Unlock Reopened Issues/PRs"

on:
  pull_request:
    types:
      - reopened
  issues:
    types:
      - reopened

jobs:
  lock:
    runs-on: ubuntu-latest

    steps:
      - uses: chxseh/action-lock-unlock@v1.0.0
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          number: ${{ github.event.pull_request.number || github.event.issue.number }}
          lock: false
```
