Azure infrastructure guidlines

# Resource groups

* Create resource group for a product
* Add `Rg` suffix to the resource group name
* Use CamelCase naming style for the resource groups
* If there are resources shared by several projects, create the resource group `ShardedRg`
* Use `OperationsRg` for resources needed to run company operational services

# Resource tags

* Every resource should have next tags:
  * `full-name` (required) - full name of the resource without abbreviations
  * `owner` (required) - who have created or requested to create the resource (example: `kryazantsev`)
  * `component` (optional) - system component which depends on the resource. If the resource is used by the single component.
