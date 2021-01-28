Azure infrastructure guidlines

# Management groups

* Use management group to unite all subscriptions
* Add region constraint to the management group, so all resources in all the subscriptions can be created only in the given region
  * Use `Western Europe`

# Subscriptions

* Create a subscription for an environment
  * Use environment name as a subscription name (`Development`, `Test`, `Production`)
* Place company operational resources in a separate subscription
  * Use `Operational` name for it

# Resource groups

* Create a resource group for a product
* Add `Rg` suffix to the resource group name
* Use CamelCase naming style for the resource groups
* If there are resources shared by several projects, create the resource group `ShardedRg`

# Resource tags

* Every resource should have next tags:
  * `full-name` (required) - full name of the resource without abbreviations
  * `owner` (required) - who have created or requested to create the resource (example: `kryazantsev`)
  * `component` (optional) - system component which depends on the resource. If the resource is used by the single component.
