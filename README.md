# kustomize-helm-mixin

This is a DRY (short for Don't Repeat Yourself) repository, which needs the hydration process to render the configs.

It includes a kustomization.yaml file.
The kustomization.yaml file will first inflate a remote Helm chart, and then apply kustomization on the inflated charts.

You can manually run `kustomize` to preview the rendered manifests:
```console
mkdir manifests
kustomize build --enable-helm --output=manifests
```

You can also run `nomos hydrate` to preview the result:
```console
nomos hydrate --source-format=unstructured --output=manifests
```
