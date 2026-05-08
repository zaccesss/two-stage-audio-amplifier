# Contributing

Commit messages, issue titles and PR descriptions for this project.

---

## Commit Messages

### Format

```
type: subject

Optional body (blank line after subject).
Explain what changed and why, not how.
```

### Types

| Type | When to use |
|---|---|
| `feat` | New content or capability |
| `fix` | Correcting an error |
| `docs` | README, comments or documentation only |
| `refactor` | Restructure without changing content |
| `chore` | Tooling, config or file organisation |
| `style` | Formatting or whitespace only |

### Rules

- Subject line 72 characters or fewer
- Imperative mood: `add` not `added`
- No capital letter after the colon
- No full stop at the end
- Body explains the why, not the how

---

## Issue Titles and Descriptions

### Title format

```
type: short description of what needs doing
```

### Labels

| Type | Label |
|---|---|
| `feat` | `enhancement` |
| `fix` | `bug` |
| `docs` | `documentation` |
| `chore` | `chore` |

### Description template

```
## What
A short sentence explaining what this issue covers.

## Why
Why does this need doing?

## Acceptance criteria
- [ ] First thing that must be true when this is done
- [ ] Second thing

## Notes
Anything extra: links, related issues, edge cases.
```

---

## Pull Request Titles and Descriptions

### Title format

```
type: short description
```

### Description template

```
## Summary
One or two sentences explaining what this PR does.

## Changes
- Short bullet for each meaningful change

## How to test
Step-by-step instructions for verifying the change.

## Related issue
closes #NUMBER

## Notes
Trade-offs made, things left out, follow-up issues.
```

---

## Session Workflow

```
1. Create issue       type: description | pick label | fill template
2. Create branch      git checkout -b type/short-description
3. Do the work        git add <files> && git commit -m "type: description"
4. Push               git push origin your-branch-name
5. Open PR            title matches issue | fill template | closes #NUMBER
6. Merge              Merge PR > Delete branch > git checkout main > git pull
```
