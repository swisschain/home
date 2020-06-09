# Swisschain: Home

Home of Swisschain products development

## Products

* [Sirius](https://github.com/swisschain/Sirius)

## Developing

To develop a feature for a Swsschain product you have to:

* Add a story to the corresponding product into [Sisschain Jira](https://swisschain.atlassian.net/) or get existing story and move to the `In Progress` state.
* Create a feature-branch named `dev-[TASK-NUMBER]-short-task-description` in the GitHub repository.
  * If you want to spread the work accross several people, create branches for each sub-task in the story.
  * Start each sub-task branch from the `dev-*` branch. Name sub-task branches `sub-[TASK-NUMBER]-short-description`
  * Once sub-task is done, merge it to the `dev-*` branch. You can do it without a PR.
* Once you'll push changes to the feature-branch, the update will be built and deployed to the dev environment via GitHub actions pipeline. `dev` tag is used for the Docker images built for the dev environment.
* Test the feature on the dev environment by yourself. Once you're sure that the feature is ready, rise a PR of the `dev-*` branch into the `master` branch and assign it to the owners of the repository.
* Once PR is reviewed and merged into the test, release a new service version using the GitHub releases and update Docker image version tag in the 'test' branch of the test/prod repository of the corresponding product.
* Ensure that your updates are deployed to the test environment and move the story to 'Testing' state in Jira.

## Releasing
