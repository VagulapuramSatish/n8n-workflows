## High-Value Lead Tracker – GitHub Stars Automation
This repository contains an n8n workflow that automatically tracks influential users who star a specific GitHub repository. “Influential” is determined by their follower count, so you can identify potential high-value leads efficiently.

***Mission***
Automatically capture when someone with many followers stars your GitHub repository, and store or notify your team for further engagement.

***Prerequisites***
Before running the workflow, you need:
- n8n instance – self-hosted or cloud.
- GitHub API token – for fetching stargazer info.
- OpenRouter API key – for optional AI enrichment or notifications.
- Discord Webhook URL – for sending alerts when high-value leads are detected.

***Setup Instructions***
1. Import the Workflow
- Open your n8n editor.
- Click Import → Paste JSON.
- Paste the workflow JSON from this repo.

2. Add Credentials
Before running the workflow, configure these credentials in n8n:
1. GitHub API Token
- Go to Settings → Credentials → Create New.
- Select GitHub Personal Access Token.
- Enter your token with repo:read and user:read scopes. 
2. OpenRouter API Key (optional)
- Go to Settings → Credentials → Create New.
- Select HTTP Request or OpenRouter integration.
- Add your API key.
3. Discord Webhook
- Go to your Discord server → Integrations → Webhooks → New Webhook.
- Copy the Webhook URL.
- Add it to n8n as Webhook Credential.

3. Configure Workflow Nodes
- GitHub Trigger Node – listens for new stars on the target repo.
- Filter Node – checks if the stargazer has followers above your “high-value” threshold.
- Optional AI Node – enriches lead data via OpenRouter.
- Discord Node – sends a notification for each high-value lead.

4. Activate Workflow
Turn the workflow ON in n8n.
Test by starring the repository from an account with high followers to confirm alerts are sent.

***Notes***
Adjust follower thresholds to fit your target audience.
Keep credentials secret; never store them in the workflow JSON.
You can extend this workflow to other platforms like Slack, email, or CRM.

***Example Use Case***
- Target Repo: your-org/high-value-project
- High-value threshold: >1000 followers
- Result: When a GitHub user with 2000 followers stars the repo, n8n triggers a Discord message to your sales team.
