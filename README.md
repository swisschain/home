# Swisschain: Home

Home of Swisschain products development

## Products

* [Sirius](https://github.com/swisschain/Sirius)

## Developing and releasing process

To develop a feature for a Swsschain product or fix a bug you have to follow given guidline.

* In Jira
  * **Project manager** or **QA Engineer** should add a `Story` or an `Bug` to the corresponding product into [Swisschain Jira](https://swisschain.atlassian.net/).
  * **Developer** should move the `Story`/`Bug` to the `In Progress` state once work is started.
  * **Developer** and/or **Project Architect** should add a `Sub-task` for each component which should be updated to complete the `Story`/`Bug`.
  * **Developer** should move each `Sub-task` to the `In Progress` state once the work on the particular component is started.
* In GitHub
  * **Developer** should create a feature-branch named `dev-[STORY/BUG-NUMBER]-short-task-description` from the `master` branch in the GitHub repository of the particular component. Note, that the branch prefix should contain `Story`/`Bug` number, not `Sub-task`.
  * Once **Developer** pushed changes to the `dev-*` branch, the update will be built and deployed to the dev environment via GitHub actions pipeline. `dev` tag is used for the Docker images built for the dev environment.
  * **Developer** should test the feature on the dev environment by himrself. Once **Developer** sure that the feature is ready, he should rise a PR of the `dev-*` branch into the `master` branch and assign it to the owners of the repository.
  * Once **Owners of the repository** have reviewed the PR they should merge it into the `master` branch.
  * **Developer** should release a new service version using the GitHub releases.
  * Once all components related to the `Storey`/`Bug` are ready, the **Developer** should update version tag of the corresponding Docker images in the `master` branch of the test/prod infrastructure repository of the corresponding product.
  * **Developer** should add a draft beta release in the test/prod infrastructure repository or update it if it's already exists. In the case if there is no draft beta release yet and there are released beta releases of the same version, the description of the new draft beta release should be copied from the recent released beta release. Developer should update description of the draft beta release: 
   * Add the `Story`/`Bug` number to the `Tasks` section
   * Describe new/updated settings keys and how to configure it in the `Settings` section
   * Describe additional manual work required in order to release the update
* In Jira
  * **Developer** should add a sub-task to test the `Story`/`Bug` and assign it to the **QA Engineer**
  * **QA Engineer** should move the sub-task to the the `Story`/`Bug` to the `In Progress` state once he is ready to start the testing
* In GitHub
  * **QA Engineer** should mark the beta release as a 'pre release' and publish it. Publishing the release will trigger deployment of the update to the test environment via GitHub actions.
* In Test environment
  * Once the beta release is deployed, **QA Engineer** should test all not tested yet the 'Stories'/'Bugs' which the release contains.
 
 TODO:

## Common auxilary services

| Service | Dev build and publish | Master build | Release |
| ------------- |-----|-----|-----|
| [Messaging.Pulsar](https://github.com/swisschain/Messaging.Pulsar) | ![Dev build](https://github.com/swisschain/Messaging.Pulsar/workflows/CI%20dev%20build/badge.svg) | ![Validate master](https://github.com/swisschain/Messaging.Pulsar/workflows/Validate%20master/badge.svg) | ![Release Service](https://github.com/swisschain/Messaging.Pulsar/workflows/Release%20Service/badge.svg) |
