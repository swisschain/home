# Kubernetes Upgrade

15.11 to 16.13 upgrade:

* Update apiVersion of deploymets (replace "apiVersion: extensions/v1beta1" by "apiVersion: apps/v1") manually or by script:
```bash
for i in $(grep -rn "apiVersion: extensions" ./|awk -F: '{print $1}'); do echo $i;cp $i $i.tmp;sed 's#apiVersion: extensions/v1beta1#apiVersion: apps/v1#g' $i.tmp > $i;rm $i.tmp; done
```
* Run new version of Dashboard (example: https://github.com/swisschain/monitoring-kubernetes/tree/dev/Monitoring-Dashboard)
* Upgrade Kubernetes manually at Azure Portal or by Azure CLI

## Upgrade manually at Portal, upgrade node pools one by one

* Go to Kubernetes object Configuration tab, at Kubernetes version select 1.16.13 and click Save (during this process access to nodes by kubectl can be lostied, all services runned at nodes will be work as before)
* Go Node polls tab, clicl on "..." right side context menu of nodes pool you need to upgrade and click Upgrade, select 1.16.13 Node pool Kubernetes version and click apply (during tshis process all services will be moved to new node and after update current node moved back)
