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

## Helm Chart Values

### Openhexa App values:

| Parameter                                 | Description                                   | Default                                                 |
|-------------------------------------------|-----------------------------------------------|---------------------------------------------------------|
| `app.config.allowedHosts`                 | Set `ALLOWED_HOSTS`                           | `*`                                                     |
| `app.config.newFrontendDomain`            | Set `NEW_FRONTEND_DOMAIN`                     | `app.openhexa.local`                                    |
| `app.config.csrfTrustedOrigins`           | Set `CSRF_TRUSTED_ORIGINS`                    | `http://app.openhexalocal`                              |
| `app.config.sessionCookieDomain`          | Set `SESSION_COOKIE_DOMAIN`                   | `http://app.openhexalocal`                              |
| `app.config.notebooksUrl`                 | Set `NOTEBOOKS_URL`                           | `http://notebooks.openhexa.local`                       |
| `app.config.useHttps`                     | Enable security                               | `true`                                                  |
| `app.config.debug`                        | Enable debug                                  | `false`                                                 |
| `app.deployment.image`                    | Openhexa app image                            | `blsq/openhexa-app`                                     |
| `app.deployment.tag`                      | Openhexa app tag                              | `latest`                                                |
| `app.ingress.annotations.kubernetes.io/ingress.class`| Ingress controller                 | `nginx`                                                 |
| `app.ingress.host`                        | Url of Openhexa App                           | `api.openhexa.local`                                    |
| `app.ingress.tls.secretName`              | Web Ingress TLS                               | `""`                                                    |
| `app.postgresql.enabled`                  | Deploy Postgresql with the Chart              | `false`                                                 |
| `app.postgresql.host`                     | Host of app database to use                   | `app-postgresql-service`                                |
| `app.postgresql.port`                     | Postgres port                                 | `5432`                                                  |
| `app.postgresql.db`                       | App postgres database to use                  | `app`                                                   |
| `app.postgresql.user`                     | App postgres user to use                      | `admin`                                                 |


### Openhexa Frontend values:

| Parameter                                 | Description                                   | Default                                                 |
|-------------------------------------------|-----------------------------------------------|---------------------------------------------------------|
| `frontend.config.graphqlEndpoint`         | Set `GRAPHQL_ENDPOINT`                        | `http://api.openhexa.local/graphql/`                    |
| `frontend.config.fallbackUrl`             | Set `FALLBACK_URL`                            | `http://api.openhexa.local`                             |
| `frontend.deployment.image`               | Openhexa frontend image                       | `blsq/openhexa-frontend`                                |
| `frontend.deployment.tag`                 | Openhexa frontend tag                         | `latest`                                                |
| `frontend.ingress.annotations.kubernetes.io/ingress.class`| Ingress controller            | `nginx`                                                 |
| `frontend.ingress.host`                   | Url of Openhexa frontend                      | `app.openhexa.local`                                    |
| `frontend.ingress.tls.secretName`         | Web Ingress TLS                               | `""`                                                    |
