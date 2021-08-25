# kustomize-helm-mixin

This is a DRY (short for Don't Repeat Yourself) repository, which needs the hydration process to render the configs.

It includes a kustomization.yaml file.
The kustomization.yaml file will first inflate a remote Helm chart, and then apply kustomization on the inflated charts.

The kustomization.yaml file defines using the `render-helm-chart` function to inflate the two Helm charts.
Therefore, the binary has to be installed before rendering:
`go install github.com/GoogleContainerTools/kpt-functions-catalog/functions/go/render-helm-chart@v0.1.0`

You can manually run `kustomize` to preview the rendered manifests:
```console
mkdir manifests
kustomize build --enable-alpha-plugins --enable-exec --output=manifests
```

You can also run `nomos hydrate` to preview the result:
```console
nomos hydrate --source-format=unstructured --output=manifests
```

To validate the hydrated configs, run:
```console
nomos vet --source-format=unstructured
```

You can save the hydrated output in the validation process via `--keep-output`:
```console
nomos vet --source-format=unstructured --keep-output --output=manifests
```
