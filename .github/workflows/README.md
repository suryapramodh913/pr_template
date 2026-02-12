# GitHub Workflows

## Greeting Agent Workflow

The **Greeting Agent** workflow (`greeting-agent.yml`) is a friendly automation that greets users and displays their last commit information.

### Features

- 🎉 Greets users by their GitHub profile name
- 📝 Retrieves and displays the user's last commit in the repository
- 📊 Creates a summary report in the workflow run
- 🔧 Can be triggered manually or automatically

### Triggers

The workflow runs on:

1. **Manual trigger** (`workflow_dispatch`): 
   - Go to Actions → Greeting Agent → Run workflow
   - Optionally specify a username to greet (defaults to the triggering user)

2. **Push to main branch**: Automatically greets the user who pushed

3. **Pull request**: Automatically greets the PR author

### What It Does

1. **Fetches User Information**: Gets the GitHub profile details of the user
2. **Retrieves Last Commit**: Finds the most recent commit by that user in the repository
3. **Displays Greeting**: Shows a formatted greeting message with:
   - User's name
   - Commit SHA
   - Commit message
   - Commit date
   - Link to the commit

### Output

The workflow produces:
- Console output with a formatted greeting message
- A GitHub Actions summary with markdown-formatted information

### Usage

#### Manual Run

```bash
# Using GitHub CLI
gh workflow run greeting-agent.yml

# With a specific username
gh workflow run greeting-agent.yml -f username=octocat
```

#### Automatic Runs

The workflow automatically runs when:
- Code is pushed to the main branch
- A pull request is opened or updated

### Requirements

- GitHub token with `contents: read` permission (provided automatically)
- Repository must have at least one commit

### Example Output

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                          🎉 GREETING AGENT 🎉                            ║
╚═══════════════════════════════════════════════════════════════════════════╝

Hello, John Doe! 👋

Welcome! I'm your friendly greeting agent, here to acknowledge your great work!

📝 Your Last Commit Information:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  📌 Commit SHA: abc123def456...
  
  💬 Message: Add new feature
  
  📅 Date: 2026-02-12T16:00:00Z
  
  🔗 Link: https://github.com/owner/repo/commit/abc123def456...

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Keep up the excellent work! 🚀
```

### Based On

This workflow is based on the custom Copilot agent defined in `.github/agents/my-agent.agent.md`.
