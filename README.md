# daily-worker

This repository contains a GitHub Actions workflow that increments a counter and commits the changes to GitHub daily, on every push to the `main` branch, and when manually triggered.

## Workflow Description

The workflow is defined in the `.github/workflows/update-counter.yml` file and performs the following steps:

1. **Checkout Repository**: Uses the `actions/checkout@v2` action to checkout the repository.
2. **Fetch GitHub User Details**: Uses the `actions/github-script@v6` action to fetch the GitHub user details (name and email) of the repository owner.
3. **Set Up Git**: Configures Git with the fetched user name and email.
4. **Increment Counter**: Increments the value in the `counter.txt` file.
5. **Commit and Push Changes**: Commits the incremented counter value and pushes the changes to the repository.

## Workflow Triggers

The workflow is triggered by the following events:
- **Scheduled**: Runs daily at midnight (UTC).
- **Push**: Runs on every push to the `main` branch.
- **Manual Dispatch**: Can be manually triggered using the `workflow_dispatch` event.

## Devcontainer Setup

This repository includes a devcontainer setup to provide a consistent development environment. The devcontainer is configured with the following extensions:

- GitHub Actions extension
- GitHub Copilot Chat extension

To use the devcontainer, ensure you have Visual Studio Code and the Remote - Containers extension installed. Then, open the repository in Visual Studio Code and select the option to reopen in the container.

## Secrets

The following secrets are required for the workflow to function correctly:
- `PAT_TOKEN`: A personal access token with the necessary permissions to push changes to the repository.

## Environment Variables

The following environment variables are used in the workflow:
- `REPO_OWNER`: The owner of the repository, automatically set using the `github.repository_owner` context.
- `PAT_TOKEN`: The personal access token for authentication.