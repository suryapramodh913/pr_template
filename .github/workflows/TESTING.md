# Testing the Greeting Agent Workflow

## Prerequisites

1. Merge the PR to the main branch
2. Ensure you have GitHub CLI installed (optional for manual testing)

## Testing Methods

### Method 1: Manual Trigger (After Merge)

#### Using GitHub Web UI
1. Go to your repository on GitHub
2. Click on the **Actions** tab
3. Select **Greeting Agent** from the workflows list
4. Click **Run workflow** button
5. (Optional) Enter a username to greet, or leave blank to greet yourself
6. Click **Run workflow** to execute
7. Wait for the workflow to complete
8. Click on the workflow run to see results

#### Using GitHub CLI
```bash
# Greet yourself (uses your GitHub username)
gh workflow run greeting-agent.yml

# Greet a specific user
gh workflow run greeting-agent.yml -f username=octocat

# View the latest run
gh run list --workflow=greeting-agent.yml

# View logs of the latest run
gh run view --log
```

### Method 2: Automatic Trigger on Push

1. Make any change to a file
2. Commit and push to main branch
   ```bash
   echo "# Test" >> README.md
   git add README.md
   git commit -m "Test greeting workflow"
   git push origin main
   ```
3. Go to Actions tab
4. See the workflow automatically triggered
5. View the greeting for the commit author

### Method 3: Automatic Trigger on Pull Request

1. Create a new branch
   ```bash
   git checkout -b test-greeting
   echo "# Test PR" >> README.md
   git add README.md
   git commit -m "Test PR greeting"
   git push origin test-greeting
   ```
2. Open a pull request on GitHub
3. Go to Actions tab
4. See the workflow automatically triggered
5. View the greeting for the PR author

## Expected Output

### Console Output
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                          🎉 GREETING AGENT 🎉                            ║
╚═══════════════════════════════════════════════════════════════════════════╝

Hello, [User Name]! 👋

Welcome! I'm your friendly greeting agent, here to acknowledge your great work!

📝 Your Last Commit Information:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  📌 Commit SHA: [40-character SHA]
  
  💬 Message: [Commit message]
  
  📅 Date: [ISO 8601 timestamp]
  
  🔗 Link: [GitHub commit URL]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Keep up the excellent work! 🚀
```

### Summary Output
In the Actions tab, you'll see a markdown-formatted summary with:
- User profile link
- Commit details in a structured format
- Clickable links to the commit

## Troubleshooting

### Workflow doesn't appear in Actions
- **Cause:** PR not merged to main branch yet
- **Solution:** Merge the PR, wait a moment, then refresh the Actions page

### "No commits found" message
- **Cause:** The specified user hasn't committed to this repository
- **Solution:** Use a username that has commits in the repository

### API rate limit errors
- **Cause:** Too many API calls in a short time
- **Solution:** Wait a few minutes before running again

### Permission errors
- **Cause:** Workflow needs `contents: read` permission
- **Solution:** Already configured in the workflow file

## Validation Checklist

After running the workflow, verify:

- [ ] Workflow completes successfully (green checkmark)
- [ ] Console output shows formatted greeting
- [ ] User name is correct
- [ ] Commit SHA is shown (if user has commits)
- [ ] Commit message is displayed
- [ ] Commit date is shown
- [ ] Commit URL is valid and clickable
- [ ] Summary section is generated
- [ ] No errors in the logs

## Performance

Expected execution time: 10-30 seconds depending on repository size and GitHub API response time.

## Next Steps

After successful testing:
1. Consider adding workflow status badge to README
2. Customize greeting message if desired
3. Add cron schedule for periodic greetings (optional)
4. Extend with additional user statistics (optional)

## Badge (Optional)

Add this to your README to show workflow status:
```markdown
![Greeting Agent](https://github.com/suryapramodh913/pr_template/actions/workflows/greeting-agent.yml/badge.svg)
```
