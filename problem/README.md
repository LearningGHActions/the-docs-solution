# The Docs

You are working for CorpX. The docs team have asked for your support in developing integration and deployment workflows for CorpX's internal knowledge base. The team has been using a manual process to update and publish these docs and they are looking to automate the process.

## Requirements

The docs team has asked for the following requirements:

### For the Integration Workflow

- Must be triggered by at least these 2 events:
  - when a new PR is created
  - when a PR is merged into the main branch

> [!TIP]
> Revisit the events that trigger workflow runs in GitHub Actions.

- Must run a linter (eslint) to check for any syntax errors in the markdown files
- Must run all the scripts in the `script/` directory in parallel and fail if any of the scripts fail
- Must build all the necessary assets to make sure the build succeeds

> [!TIP]
> The `package.json` file has a lot of information about the build scripts.

- Must cache the `node_modules` directory to speed up the build process
  - Must bust the cached `node_modules` directory if the `package.json` file has changed

### For the Deployment Workflow

- Must run when a commit has been pushed to the `main` branch
- Must never run if the integration workflow has failed
- Must never run if there are no changes introduced

> [!TIP]
> Think about how to use workflow contexts, outputs, and expressions to achieve this.

- Must deploy to the GitHub Pages environment only

> [!TIP]
> If GitHub Pages is not enabled, you can enable it in the repository settings.

- Must not have more than 1 run at a time (concurrency limit of 1)
  - If a deployment is already running and a new commit is pushed, the deployment should be cancelled and a new deployment should start
- Must upload a `tar.gz` file of the generated assets as an artifact to the workflow run

> [!TIP]
> Don't reinvent the wheel. Use marketplace actions to help you achieve your objectives.

- Must use the `GH_TOKEN` secret to authenticate with GitHub
- Must run a post-deployment test by calling the GitHub Pages URL and checking for a 200 status code

> [!TIP]
> Think how you can leverage the `shell` override to help you with this task.

- Must support a `force deployment` option (think how you can use `workflow_dispatch` events)
  - This option should be a boolean input and if set to true, the deployment should run even if there are no changes were pushed to `main`

## General guidelines

- The workflows should be as efficient as possible. You must reuse as much as you can from the solutions available to you.
- All workflow runs and should have a strict timeout of `20 minutes` and should fail if the timeout is reached. Timeout includes the integration and deployment runs.
- If you use any third-party actions, make sure to pin the action to a full length commit SHA. Read more about [pinning actions](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions#using-third-party-actions).