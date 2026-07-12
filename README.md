# escalations

Issue escalations for customer service and staff

## How to Submit an Escalation

To submit a new escalation, use the [issue form](../../issues/new/choose) which will guide you through providing all necessary information.

**Note:** A GitHub account is required to submit escalations.

The escalation form includes:

- **Short summary**: One line that appears as the issue title and in notifications
- **Criticality**: Choose "THIS IS A CRITICAL ISSUE" only for service outages or critical problems requiring immediate attention; otherwise "This is not a critical issue"
- **Affected Tool**: Which product or tool is experiencing the issue (Footballguys.com, Infrastructure, League Sync, Draft Dominator, League Dominator, DFS Multi-Lineup Optimizer, DFS Single Lineup Builder, or Other)
- **Customer Username or Email**: Contact information for the affected customer
- **Zendesk Ticket Link**: Related support ticket (if applicable)
- **Basecamp Thread Link**: Related discussion (if applicable)
- **How to see this issue (numbered steps)**: Reproduction path; each step numbered, one action per step, starting from the beginning (e.g. open site or sign in)
- **What should have happened?**: Expected outcome in plain language
- **What happened instead?**: Actual outcome, including exact error text when applicable
- **Customer Impact**: How the issue affects the customer or business

## Quick Start

1. Click on the ["Issues" tab](../../issues)
2. Click "New Issue"
3. Select "Escalation Request"
4. Fill out the form with all relevant details
5. Submit the issue

The escalation is automatically triaged (label + assignee) and added to the [Escalations project](https://github.com/orgs/footballguysdotcom/projects/5).

For some products, the issue is **moved** (GitHub transfer) into the product repository after filing. You still use the Escalations project board to track work; you do not need the `escalations` repo issue list.

| Affected Tool | Issue lives in |
|---|---|
| Draft Dominator | `footballguysdotcom/draft-dominator` (also added to [Draft Dominator 3.0](https://github.com/orgs/footballguysdotcom/projects/8)) |
| Footballguys.com | `footballguysdotcom/fbgsite` |
| League Sync | `footballguysdotcom/fbg-cloud-server` |
| League Dominator, Infrastructure, DFS tools, Other | `footballguysdotcom/escalations` (no transfer) |

## Automation secret (`PROJECT_TOKEN`)

Workflows use the repository secret **`PROJECT_TOKEN`**. It must be a personal access token (or fine-grained token) that can:

- **Issues write** on `escalations`, `draft-dominator`, `fbgsite`, and `fbg-cloud-server` (label, assign, and **transfer** issues)
- **Org Projects write** for the Escalations project (project number 5) and Draft Dominator 3.0 (project number 8)

Classic PAT scopes: `repo` + `project`. Fine-grained: Issues (read/write) on those four repositories, plus Organization permissions for Projects (read/write).

The same secret name is used on the product repos that run **Set time to resolve on close** when a transferred escalation is closed there. Prefer an **organization secret** named `PROJECT_TOKEN` visible to those repos, or copy the same token as a repo secret in each.

**Required on product repos (default branch):** add `PROJECT_TOKEN` to `draft-dominator`, `fbgsite`, and `fbg-cloud-server`. Without it, intake transfer still works (it runs on `escalations`), but close metrics on transferred issues will fail with `Input required and not supplied: github-token`. Issue-triggered workflows must live on each repo’s **default** branch (`main` for draft-dominator, `production` for fbgsite, `master` for fbg-cloud-server).

## Project board (optional fields)

On the [Escalations project](https://github.com/orgs/footballguysdotcom/projects/5), you can add these custom fields so workflows can populate them and views can be sorted:

- **Time to resolve (days)** (Number) – set when an issue is closed; already in use.
- **Filed date** (Date) – set when an issue is added to the project; use to sort/open views by when issues were filed.
- **Resolved date** (Date) – set when an issue is closed; use to sort the **Closed** list by resolution date (add the column to the Closed view, then click the column header to sort).
