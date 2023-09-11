# azure-terraform-modules

# Tagging the TF Modules Repo
This GitHub Actions workflow is designed to automatically tag the TF Modules repository when specific conditions are met. It performs the following actions:

1. Triggers the workflow on a push to the main branch, except for changes in the .github/ directory.
2. Triggers the workflow when a pull request is closed.
3. Allows manual triggering of the workflow through the workflow_dispatch event.

# Workflow Steps
## Reading the Commit Message and Pushing the New Tag
This step runs on a designated runner (CAI-Enterprise) and consists of the following actions:

1. Checks out the repository code using actions/checkout@v3.
2. Extracts the commit message from the most recent commit using git log.
3. Validates the commit message to ensure it contains a version number in the format vX.Y.Z.
4. If the commit message contains a valid version number, it sets the VERSION_NUMBER output variable.
5. If the commit message doesn't contain a version number, the workflow is skipped with an exit code of 78.
6. Tags the current repository code with the extracted version number.
7. Pushes the newly created tag to the remote repository.

# Workflow Triggers
This workflow is triggered under the following conditions:

1. Push: The workflow is triggered when a push event occurs on the main branch, excluding changes in the .github/ directory.
2. Pull Request: The workflow is triggered when a pull request is closed.
3. Workflow Dispatch: The workflow can also be manually triggered using the workflow_dispatch event.

Note: The workflow requires specific conditions to be met before tagging the repository with a version number. The commit message must contain a version number in the format vX.Y.Z. If the version number is not present or is set to 'skip', the workflow will be skipped.
