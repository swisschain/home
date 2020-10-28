# Swisschain: Home

Home of Swisschain products development

## Products

* [Sirius](https://github.com/swisschain/Sirius)

## Development and release process

To develop a feature for a Swsschain product or fix a bug you have to follow given guidline.

* On GitHub
  * **Release manager** creates the new `version-branch` in the infrastructure repository of the product and set it as the default branch. Name pattern for the branch is `versions/{major}.{minor}.{patch}`
  * **Release manager** creates a draft beta-release in the infrastructure repository of the productvia GitHub Releases. Name pattern for the release is `{major}.{minor}.{patch}-beta.{revision}`. Template for the release description is **TODO**.
* On Jira
  * **Project manager** or **QA Engineer** adds a `Story` or a `Bug` to the corresponding product into [Swisschain Jira](https://swisschain.atlassian.net/).
  * **Developer** moves the `Story`/`Bug` to the `In Progress` state once work is started.
  * **Developer** and/or **Project Architect** adds a `Sub-task` for each component which should be updated to complete the `Story`/`Bug`.
  * **Developer** moves each `Sub-task` to the `In Progress` state once the work on the particular component is started.
* On GitHub
  * **Developer** creates a `feature-branch` named `dev-{STORY/BUG-NUMBER}-short-task-description` from the `master` branch in the GitHub repository of the particular component. Note, that the branch prefix should contain `Story`/`Bug` number, not `Sub-task`.
  * Once the **Developer** has pushed changes to the `feature-branch`, the updated component will be built and deployed to the dev environment via GitHub actions pipeline. *`dev` tag is used for the Docker images built for the dev environment*.
  * **Developer** tests the feature on the dev environment by himrself. Once the **Developer** sure that the feature is ready, he creates a PR of the `feature-branch` into the `master` branch and assigns it to the **Repository owners**.
  * Once the **Repository owners** have reviewed the PR they merges it into the `master` branch.
  * **Developer** releases the new service version via GitHub Releases. Name patter for the release is `service-{major}.{minor}.{patch}`.
  * Once all components related to the `Storey`/`Bug` are ready, the **Developer** updates version tag of the corresponding Docker images in the current `version-branch` of the infrastructure repository of the product.
  * If it's needed to update the infrastructure of the product or its settings templates, the **Developer** updates `version-branch` of the infrastructure repository of the product accordingly.
  * **Developer** updates a draft beta-release in the infrastructure repository or adds the new draft beta-release if there is no draft beta-release yet. In the case if there is no draft beta-release the description of the new draft beta-release should be copied from the recently published beta-release of the same version. Developer should update description of the draft beta-release: 
   * Add the `Story`/`Bug` number to the `Tasks` section
   * Describe new/updated settings keys and how to configure it in the `Settings` section
   * Describe additional manual work required in order to release the update
   * Describe order of the components to add/update/remove
* On Jira
  * **Developer** adds a sub-task to test the `Story`/`Bug` and assign it to the **QA Engineer**
  * **QA Engineer** moves the sub-task to test the `Story`/`Bug` to the `In Progress` state once he is ready to start the testing and notifies **Release manager**.
* On Test environment
  * **DevOps**, **Developer** and **Release manager** executes beta-release instructions.
* On GitHub
  * **Release manager** updates the beta-release description if any issues found while executing the instructions.
  * Once beta-release instructions are completely executed the **Release manager** publishes the beta-release as the `pre release`. **TODO** (should we deploy updates manually as we do it on prod?). Publishing the release will trigger deployment of the update to the test environment via GitHub actions.
* On Test environment
  * Once the beta release is deployed, **QA Engineer** tests all not tested yet 'Stories'/'Bugs' which the beta-release contains.
* On GitHub
  * Once the beta-release testing is completed and **Project manager** have decided to publish it as a stable-version, the **QA Engineer** marks the release as validated and pass it to the **DevOps** to review.
  * Once the **DevOps** has reviewed the release by comparing it with the `master` branch, he marks the release as validated and pass it to the **Release manager** to check version content.
  * Once the **Release manager** has checked the version content, he marks the release as validated.
  * **Release manager** copies the release description to the new stable-release and publishes it. Name pattern for the release is `{major}.{minor}.{patch}`.
  * **Release manager** removes all beta-releases of the version.
  * **DevOps** creates a pull request of the `version-branch` of the product infrastructure repository to the `master` branch of the forked repository related to the particular maintained instance of the product.
  * **Release manager** merges the `version-branch` to the `master` branch of the product infrastructure repository.
  * See first point.

## Common auxilary services

| Service | Dev build and publish | Master build | Release |
| ------------- |-----|-----|-----|
| [Messaging.Pulsar](https://github.com/swisschain/Messaging.Pulsar) | ![Dev build](https://github.com/swisschain/Messaging.Pulsar/workflows/CI%20dev%20build/badge.svg) | ![Validate master](https://github.com/swisschain/Messaging.Pulsar/workflows/Validate%20master/badge.svg) | ![Release Service](https://github.com/swisschain/Messaging.Pulsar/workflows/Release%20Service/badge.svg) |
