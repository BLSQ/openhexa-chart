# openhexa-chart

This repository stores in its [gh-pages branch](https://github.com/BLSQ/openhexa-chart/tree/gh-pages) packaged Helm charts for Openhexa. These packaged Helm charts are made available as a valid Helm chart repository on an automatically updated website thanks to GitHub Pages. 

## Usage

This Helm chart repository enables you to install Openhexa Helm chart directly from it into your Kubernetes cluster. Please refer to the [Openhexa Helm chart documentation](https://github.com/BLSQ/openhexa-local-hosting#openhexa).

To install the chart with the release name `openhexa`, run the following commands:

```
helm repo add openhexa https://viz.bluesquare.org/openhexa-chart/
helm repo update
helm upgrade --install openhexa openhexa/openhexa -f values.yaml -f values.default.yaml 
```

To upgrade the chart with the release name `openhexa`:

```
helm upgrade openhexa openhexa/openhexa
```

To uninstall the openhexa deployment:

```
helm uninstall openhexa 
```


