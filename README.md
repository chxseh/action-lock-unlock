<div align="center">
<h1>Lock/Unlock a PR/Issue<br>
<a href="https://github.com/chxseh/action-lock-unlock/stargazers"><img alt="Stars" src="https://img.shields.io/github/stars/chxseh/action-lock-unlock"></a>
<a href="https://github.com/chxseh/action-lock-unlock/issues"><img alt="Issues" src="https://img.shields.io/github/issues/chxseh/action-lock-unlock"></a>
<a href="https://github.com/chxseh/action-lock-unlock/pulls"><img alt="Pull Requests" src="https://img.shields.io/github/issues-pr/chxseh/action-lock-unlock"></a>
<a href="https://github.com/chxseh/action-lock-unlock/network"><img alt="Forks" src="https://img.shields.io/github/forks/chxseh/action-lock-unlock"></a>
<a href="https://github.com/chxseh/action-lock-unlock/blob/main/LICENSE.md"><img alt="License" src="https://img.shields.io/github/license/chxseh/action-lock-unlock"></a>
</h1></div>

Based on [sudo-bot/action-pull-request-lock](https://github.com/sudo-bot/action-pull-request-lock)

> **Warning**
>
> Bots cannot trigger other workflows, so if you have another workflow that merges/closes a PR/Issue, this workflow would not run.

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
      - uses: chxseh/action-lock-unlock@v1.0.1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          number: ${{ github.event.pull_request.number || github.event.issue.number }}
          lock: true
          lock-reason: resolved
          # The lock-reason can be: off-topic,too heated,resolved,spam
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
  unlock:
    runs-on: ubuntu-latest

    steps:
      - uses: chxseh/action-lock-unlock@v1.0.1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          number: ${{ github.event.pull_request.number || github.event.issue.number }}
          lock: false
```
