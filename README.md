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

The following is a summary of the helm values provided by Openhexa chart.

<details>
<summary><code>app.*</code></summary>

| Parameter                                 | Description                                   | Default                                                 |
|-------------------------------------------|-----------------------------------------------|---------------------------------------------------------|
| `app.config.allowedHosts`                 | Set `ALLOWED_HOSTS`                           | `""`                                                    |
| `app.config.newFrontendDomain`            | Set `NEW_FRONTEND_DOMAIN`                     | `""`                                                    |
| `app.config.csrfTrustedOrigins`           | Set `CSRF_TRUSTED_ORIGINS`                    | `""`                                                    |
| `app.config.sessionCookieDomain`          | Set `SESSION_COOKIE_DOMAIN`                   | `""`                                                    |
| `app.config.notebooksUrl`                 | Set `NOTEBOOKS_URL`                           | `""`                                                    |
| `app.config.useHttps`                     | Enable security                               | `true`                                                  |
| `app.config.debug`                        | Enable debug                                  | `false`                                                 |
| `app.deployment.image`                    | Openhexa app image                            | `blsq/openhexa-app`                                     |
| `app.deployment.tag`                      | Openhexa app tag                              | `""`                                                    |
| `app.ingress.annotations`                 | Web Ingress annotations                       | `{}`                                                    |
| `app.ingress.host`                        | Url of Openhexa App                           | `""`                                                    |
| `app.ingress.tls.secretName`              | Name of a Secret containing a TLS private key and certificate  | `""`                                   |
| `app.postgresql.enabled`                  | Deploy Postgresql with this Chart             | `false`                                                |
| `app.postgresql.host`                     | Host of app database to use                   | `""`                                                    |
| `app.postgresql.port`                     | Postgres port                                 | `5432`                                                  |
| `app.postgresql.db`                       | App postgres database to use                  | `""`                                                    |
| `app.postgresql.user`                     | App postgres user to use                      | `""`                                                    |
<hr>
</details>

<details>
<summary><code>frontend.*</code></summary>

| Parameter                                 | Description                                   | Default                                                 |
|-------------------------------------------|-----------------------------------------------|---------------------------------------------------------|
| `frontend.config.graphqlEndpoint`         | Set `GRAPHQL_ENDPOINT`                        | `""`                                                    |
| `frontend.config.fallbackUrl`             | Set `FALLBACK_URL`                            | `""`                                                    |
| `frontend.deployment.image`               | Openhexa frontend image                       | `blsq/openhexa-frontend`                                |
| `frontend.deployment.tag`                 | Openhexa frontend tag                         | `""`                                                    |
| `frontend.ingress.annotations`            | Web Ingress annotations                       | `{}`                                                    |
| `frontend.ingress.host`                   | Url of Openhexa frontend                      | `""`                                                    |
| `frontend.ingress.tls.secretName`         | Web Ingress TLS                               | `""`                                                    |
<hr>
</details>

<details>
<summary><code>airflow.*</code></summary>

| Parameter                                 | Description                                   | Default                                                 |
|-------------------------------------------|-----------------------------------------------|---------------------------------------------------------|
| `airflowDb.enabled`                       | Deploy Postgresql with this Chart             | `false`                                                 |
| `airflow.webserver.replicas`              | Number of webservers                          | `1`                                                     |
| `airflow.webserver.defaultUser.email`     | Set initial user email                        | `""`                                                    |
| `airflow.webserver.defaultUser.username`  | Set initial user name                         | `""`                                                    |
| `airflow.webserver.defaultUser.password`  | Set initial user password                     | `""`                                                    |
| `airflow.data.metadataSecretName`         | Set connection values from a Secret           | `airflow-db-secret`                                     |
| `airflow.ingress.web.annotations`         | Web Ingress annotations                       | `{}`                                                    |
| `airflow.ingress.web.hosts`               | Url of Openhexa airflow                       | `[]`                                                    |
| `airflow.ingress.web.tls.enabled`         | Enable TLS termination for the web Ingress                     | `false`                                |
| `airflow.ingress.web.tls.secretName`      | Name of a Secret containing a TLS private key and certificate  | `""`                                   |
<hr>
</details>

<details>
<summary><code>notebooks.*</code></summary>

| Parameter                                 | Description                                   | Default                                                 |
|-------------------------------------------|-----------------------------------------------|---------------------------------------------------------|
| `notebooks.config.contentSecurityPolicy`  | Set `CONTENT_SECURITY_POLICY`                 | `""`                                                    |
| `notebooks.config.appCredentialsUrl`      | Set `APP_CREDENTIALS_URL`                     | `""`                                                    |
| `notebooks.config.logoutRedirectUrl`      | Set `LOGOUT_REDIRECT_URL`                     | `""`                                                    |
| `notebooks.postgresql.enabled `           | Deploy Postgresql with this Chart             | `false`                                                 |
| `jupyterhub.hub.config.JupyterHub.authenticator_class`| Authenticator class KubeSpawner                                | ``                                     |
| `jupyterhub.hub.db.url`                               | Notebooks postgres URL to use                                  | `""`                                   |
| `jupyterhub.hub.image.name`                           | Openhexa Jupyterhub image                                      | `blsq/openhexa-jupyterhub`             |
| `jupyterhub.hub.image.tag`                            | Openhexa Jupyterhub tag                                        | `{}`                                   | 
| `jupyterhub.singleuser.image.name`                    | Openhexa Singleuser image                                      | `blsq/openhexa-base-notebook`          |
| `jupyterhub.singleuser.image.tag`                     | Openhexa Singleuser tag                                        | `false`                                |
| `jupyterhub.ingress.annotations`                      | Web Ingress annotations                                        | `""`                                   |
| `jupyterhub.ingress.hosts`                            | Url of Openhexa notebooks                                      | `[]`                                   |
| `jupyterhub.ingress.tls.0.secretName`                 | Name of a Secret containing a TLS private key and certificate  | `""`                                   |

<hr>
</details>

<details>
<summary><code>minio.*</code></summary>

| Parameter                                 | Description                                   | Default                                                 |
|-------------------------------------------|-----------------------------------------------|---------------------------------------------------------|
| `minio.deployment.image`                  | Minio image                                   | `"minio/minio"`                                         |
| `minio.deployment.tag`                    | Minio tag                                     | `"latest"`                                              |
| `minio.ingress.annotations`               | Web Ingress annotations                       | `{}`                                                    |
| `minio.ingress.host`                      | Url of minio                                  | `""`                                                    |
| `minio.ingress.tls.secretName`            | Name of a Secret containing a TLS private key and certificate   | `""`                                  |

<hr>
</details>

## Example Helm Values to test this chart locally by deploying Postgres

### App

```
app:
  config:
    allowedHosts: "*"
    newFrontendDomain: "app.openhexa.local"
    corsAllowedOrigins: "http://app.openhexa.local"
    csrfTrustedOrigins: "http://app.openhexa.local"
    sessionCookieDomain: ".openhexa.local"
    notebooksUrl : "http://notebooks.openhexa.local"
  deployment:
    image: blsq/openhexa-app
    tag: latest
  ingress:
    annotations:
      kubernetes.io/ingress.class: "nginx"
    host: api.openhexa.local
    tls:
      secretName: ""
  postgresql:
    enabled: true
    host: app-postgresql-service
    port: 5432
    db: app
    user: admin
  
```
### Frontend

```
frontend:
  config:
    graphqlEndpoint: "http://api.openhexa.local/graphql/"
    fallbackUrl: "http://api.openhexa.local"
  deployment:
    image: blsq/openhexa-frontend
    tag: latest
  ingress:
    annotations:
      kubernetes.io/ingress.class: "nginx"
    host: app.openhexa.local
    tls:
      secretName: ""
```
### Airflow

```
airflowDb:
  enabled: true
airflow:
  webserver:
    replicas: 1
    defaultUser:
      email: "root@openhexa.org"
      username: "root@openhexa.org"
      password: "root"
  data:
    metadataSecretName: airflow-db-secret
  ingress:
    web:
      annotations:
        kubernetes.io/ingress.class: "nginx"
      hosts: 
      - airflow.openhexa.local
      tls:
        enabled: false
        secretName: """
```
### Notebooks

```
notebooks:
  config:
    contentSecurityPolicy: "frame-ancestors 'self' api.openhexa.local app.openhexa.local;"
    appCredentialsUrl: "http://api.openhexa.local/notebooks/credentials/"
    logoutRedirectUrl: "http://app.openhexa.local"
  postgresql:
    enabled: true
jupyterhub:
  hub:
    config:
      JupyterHub:
        authenticator_class:
    db:
      url: "postgresql://admin@notebooks-postgresql-service:5432/notebooks"
    image:
      name: "blsq/openhexa-jupyterhub"
      tag: "1.3.2"
  singleuser:
    image:
      name: "blsq/openhexa-base-notebook"
      tag: "0.9.9"
  ingress:
    annotations:
      kubernetes.io/ingress.class: "nginx"
    hosts:
      - notebooks.openhexa.local
    tls:
      - secretName: "" 
```
### Minio

```
minio:
  deployment:
    image: minio/minio
    tag: latest
  ingress:
    annotations:
      kubernetes.io/ingress.class: "nginx"
    host: minio.openhexa.local
    tls:
      secretName: ""
```

