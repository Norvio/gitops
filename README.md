# gitops

Desired state for the cluster, reconciled by ArgoCD.

```
apps/     ArgoCD Application manifests (one per service)
values/   Helm values per service, rendered with charts/service from Norvio/charts
```

Each Application uses two sources: the chart from `Norvio/charts` and the values
file from this repo (`ref: values`). To deploy a new image, change `image.tag`
in `values/<service>.yaml` and merge.

## Bootstrap

```
kubectl apply -f apps/
```

Applications start with manual sync. Add `syncPolicy.automated`
(`prune`, `selfHeal`) once you are comfortable with it.
