# Gate Helm Packages

Maintains the Helm packages of gate-sso.

## Using the Packages

Add packages repo in Helm:

```bash
$ helm repo add gate-sso https://gate-sso.github.io/helm-packages
```

Install `gate` package with release name `my-gate`:

```bash
$ helm install --name my-gate gate-sso/gate
```

To use custom setting please create `my-values.yaml` according to [configuration](https://github.com/gate-sso/helm-charts/tree/master/stable/gate#configuration) then use this command:

```bash
$ helm install --name my-gate --values my-values.yaml gate-sso/gate
```

## Adding New Package

1. Clone repo `https://github.com/gate-sso/helm-charts`.
2. Go to `stable/gate` folder.
3. Update the chart and app version in `Chart.yaml`.
4. Update image tag in `values.yaml`.
5. Execute `$ helm package .`, this will create file `gate-x.y.z.tgz`, where x, y, z are the new version number that automatically generated from step 3.
6. Move `gate-x.y.z.tgz` to this repo.
7. Execute `$ helm repo index . --url https://gate-sso.github.io/helm-packages`, this will update the `index.yaml` file.
8. Commit and push changes from both repo.
