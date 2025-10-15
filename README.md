# escalations
Issue escalations for customer service and staff

## How to Submit an Escalation

There are two ways to submit an escalation:

### Option 1: Public Form (No GitHub Account Required)
**Perfect for non-technical staff members**

Use our public escalation form: [https://footballguysdotcom.github.io/escalations/](https://footballguysdotcom.github.io/escalations/)

This form allows anyone to submit an escalation without needing a GitHub account. Simply fill out the form and it will automatically create an issue in this repository.

### Option 2: GitHub Issue Template (GitHub Account Required)
**For staff with GitHub accounts**

To submit a new escalation directly on GitHub, use the [issue form](../../issues/new/choose) which will guide you through providing all necessary information.

The escalation form includes:
- **Escalation Type**: Select the category of your issue
- **Priority Level**: Indicate the urgency (Critical, High, Medium, Low)
- **Customer/User Information**: Relevant contact details
- **Issue Description**: Detailed explanation of the problem
- **Steps Already Taken**: Previous troubleshooting attempts
- **Customer Impact**: How the issue affects the customer or business
- **Desired Resolution**: Expected outcome
- **Escalated By**: Your name or team

## Quick Start

1. Visit the [public form](https://footballguysdotcom.github.io/escalations/) or click on the "Issues" tab
2. If using GitHub directly, click "New Issue"
3. Select "Escalation Request"
4. Fill out the form with all relevant details
5. Submit the issue

---

## Setup Instructions (For Administrators)

To enable the public form functionality, you need to configure a GitHub Personal Access Token:

1. Go to [GitHub Settings → Tokens](https://github.com/settings/tokens)
2. Click "Generate new token (classic)"
3. Give it a descriptive name (e.g., "Escalations Form")
4. Select **only** the `public_repo` scope
5. Generate the token and copy it
6. Edit `index.html` and replace `YOUR_GITHUB_TOKEN_HERE` with your token
7. Commit and push the change

**Security Note:** The token will be visible in the source code, but since it only has `public_repo` scope and the repository is public, the risk is minimal. The token can only create issues in public repositories. You can revoke and rotate the token at any time from your GitHub settings.
