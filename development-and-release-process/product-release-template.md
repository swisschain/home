# Fixes/Improvements

**QA Engineer** should mark each story/bug with :heavy_check_mark: or :x: once it's tested.

## {EPIC-NUMBER} - {Epic description}

* {STORY-NUMBER} [Improvement] - {Story description}
* {STORY-NUMBER} [Improvement] - {Story description}
* {BUG-NUMBER} [Fix] - {Fix description}

# Settings

* Add `{New-Settings-Key-Name}` - {New settings value or how to get the value if it's a secret}
* Update `{Updated-Settings-Key-Name}` - {Updated settings value or how to get the value if it's a secret}
* Remove `{Removed-Settings-Key-Name}`

# Kubernetes secrets

* Add `{New-Secret-Service-Name}.{New-Secret-Namespace}/{New-Secret-Key-Name}` - {New kubernetes secret value or how to get the value if it's a secret}
* Update `{Updated-Secret-Service-Name}.{Updated-Secret-Namespace}/{Updated-Secret-Key-Name}` - {Updated kubernetes secret value or how to get the value if it's a secret}
* Remove `{Removed-Secret-Service-Name}.{Removed-Secret-Namespace}/{Removed-Secret-Key-Name}`

# Actions

List all actions to complete the release here. All actions should be listed in the correct order.

* {Additional preparation}
* Add settings
* Update settings
* Add Kubernetes secrets
* Update Kubernetese secrets
* Update settings service and restart it
* Add Kubernetes service `{service-name}.{service-namespace}:{service-version}`
* Update Kubernetes service `{service-name}.{service-namespace}:{service-version}`
* Remove Kubernetes service `{service-name}.{service-namespace}:{service-version}`
* Add Docker Compose service `{docker-compose-path}:{service-version}`
* Update Docker Compose service `{docker-compose-path}:{service-version}`
* Remove Docker Compose service `{docker-compose-path}:{service-version}`
* Remove settings
* Remove Kubernetese secrets
* {Additional clean-up}

# Signatures

* Use :heavy_check_mark: to mark as resolved
* Use :x: to mark as failed

| Role            | Person        | Resolution | Description |
|-----------------|---------------|-----------:|-------------|
| QA Engineer     |               |            |             |
| DevOps          |               |            |             |
| Release Manager |               |            |             |
