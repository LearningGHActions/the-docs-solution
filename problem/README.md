# The Docs

You are working for CorpX. The docs team have asked for your support in developing integration and deployment workflows for CorpX's internal knowledge base. The team has been using a manual process to update and publish these docs and they are looking to automate the process.

## Requirements

The docs team has asked for the following requirements:

### For the Integration Workflow

- Must be triggered on at least these 2 events:
  - when a new PR is created
  - when a PR is merged into the main branch
- Must run a linter (eslint) to check for any syntax errors in the markdown files
- Must build all the necessary assets to make sure the build succeeds
- Must cache the `node_modules` directory to speed up the build process
  - Must bust the cached `node_modules` directory if the `package.json` file has changed
- Must run all the scripts in the `script/` directory in parallel and fail if any of the scripts fail

### For the Deployment Workflow

- Must run when a commit has been pushed to the `main` branch
- Must never run if the integration workflow has failed
- Must never run if there are no changes introduced
- Must deploy to the GitHub Pages environment
- Must not have more than 1 run at a time (concurrency limit of 1)
  - If a deployment is already running and a new commit is pushed, the deployment should be cancelled and a new deployment should start
- Must upload a `tar.gz` file of the generated assets as an artifact to the workflow run
- Must use the `GH_TOKEN` secret to authenticate with GitHub
- Must run a post-deployment test by calling the GitHub Pages URL and checking for a 200 status code
- Must support a `force deployment` option (think how you can use `workflow_dispatch` events)
  - This option should be a boolean input and if set to true, the deployment should run even if there are no changes were pushed to `main`

## Notes and references

