# HELM PUBLISH ACTION

[![Version](https://github.com/AaronYang0628/push-helm-chart-to-oci/?label=Release)](https://github.com/AaronYang0628/push-helm-chart-to-oci/releases)
[![License](https://img.shields.io/badge/License-Apache_2.0-yellow.svg)](https://opensource.org/licenses/Apache-2.0)

Github Action to simplify Helm Chart publish into a registry.

# Usage

See [action.yml](action.yml)

```yaml
- name: Helm Publish Action
  uses: AaronYang0628/push-helm-chart-to-oci@latest
  with:
    working-dir: ${{ matrix.chart_path }}
    oci-repository: oci://${{ env.REGISTRY }}/${{ env.REPOSITORY_NAMESPACE }}
    username: ${{ env.USER }}
    password: ${{ secrets.ZJ_HARBOR_TOKEN }}
```


### Before hook

If you need to execute a command before to publish, pass it via `beforeHook` argument.
This hook is usefully if you have subchart inside your Chart and you want update it before to publish your parent chart.

```yaml
- name: Helm Publish Action
  uses: huggingface/helm-publish-action@latest
  with:
    beforeHook: cd subcharts/my-sub-chart && helm dependencies update
```
