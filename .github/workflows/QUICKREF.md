# Greeting Agent - Quick Reference

## One-Line Summary
A GitHub Actions workflow that greets users and displays their latest commit information.

## Quick Start (After Merge)
```bash
gh workflow run greeting-agent.yml
```

## Files
- `greeting-agent.yml` - The workflow
- `README.md` - User documentation
- `MIGRATION.md` - Conversion details
- `TESTING.md` - Testing guide

## Triggers
| Trigger | When | Who Gets Greeted |
|---------|------|------------------|
| Manual | Actions → Run workflow | You or specified user |
| Push | Push to main | Committer |
| PR | Open/update PR | PR author |

## What It Shows
- User's GitHub profile name
- Last commit SHA
- Commit message
- Commit date
- Link to commit

## Common Commands
```bash
# Run for yourself
gh workflow run greeting-agent.yml

# Run for specific user
gh workflow run greeting-agent.yml -f username=octocat

# View recent runs
gh run list --workflow=greeting-agent.yml

# View last run logs
gh run view --log

# Watch workflow status
gh run watch
```

## Output Locations
1. **Console**: Workflow logs (Actions → Greeting Agent → Run → Job logs)
2. **Summary**: Actions tab summary section (markdown formatted)

## Requirements
- GitHub token (automatic)
- At least one commit by user
- Merged to main branch

## Badge
```markdown
![Greeting Agent](https://github.com/suryapramodh913/pr_template/actions/workflows/greeting-agent.yml/badge.svg)
```

## Support
See full documentation in:
- `README.md` - Usage guide
- `TESTING.md` - How to test
- `MIGRATION.md` - Technical details
