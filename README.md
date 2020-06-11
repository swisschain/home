# Swisschain: Home

Home of Swisschain products development

## Products

* [Sirius](https://github.com/swisschain/Sirius)

## Developing

To develop a feature for a Swsschain product you have to:

* Add a story to the corresponding product into [Sisschain Jira](https://swisschain.atlassian.net/) or get an existing story and move it to the `In Progress` state.
* Create a feature-branch named `dev-[TASK-NUMBER]-short-task-description` from the `master` branch in the GitHub repository.
  * If you want to spread the work across several people, create a separate branch for each sub-task in the story.
  * Start each sub-task branch from the `dev-*` branch.
  * Name sub-task branche like `sub-[TASK-NUMBER]-short-task-description`.
  * Once sub-task is done, merge it to the `dev-*` branch.
* Once you'll push changes to the `dev-*` branch, the update will be built and deployed to the dev environment via GitHub actions pipeline. `dev` tag is used for the Docker images built for the dev environment.
* Test the feature on the dev environment by yourself. Once you're sure that the feature is ready, rise a PR of the `dev-*` branch into the `master` branch and assign it to the owners of the repository.
* Once PR is reviewed and merged into the `master`, release a new service version using the GitHub releases and update the Docker image version tag in the `test` branch of the test/prod repository of the corresponding product.
* Ensure that your updates are deployed to the test environment and add a sub-task to test the story in Jira.

## Releasing
