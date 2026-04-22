# Full Stack App Portal

This is a blueprint for the portal section of the [full-stack-app-blueprint](https://github.com/krateoplatformops-blueprints/full-stack-app). 

It creates five main pages:
  - A composition overview page, showing all the FullStackApps in the cluster with some of their details.
  - A composition status page, showing the status of a single composition in the cluster.
  - A composition flowchart page, showing a flowchart of the resources managed by a single composition in the cluster.
  - A composition logs page, showing the logs of the resources managed by a single composition in the cluster.
  - The composition's CNPG cluster status page, showing the status of the CNPG cluster.

## Prerequisites 

Install the [portal-admin-page](https://github.com/krateoplatformops-blueprints/portal-admin-page) to gain access to the logs endpoint:

```sh
helm install portal-admin-page portal-admin-page \
  --repo https://marketplace.krateo.io \
  --namespace krateo-system \
  --set portalBlueprintPage.installCompositionDefinition=false \
  --version 1.1.1 \
  --wait
```

## Installation

Put this chart as a dependency of the `full-stack-app` blueprint:

```yaml
# Chart.yaml
dependencies:
- name: full-stack-app-portal
  version: "1.0.0"
  repository: "https://marketplace.krateo.io"
```

Once the `full-stack-app` comoposition is created, five new portal main sections will appear in the Krateo composable portal.
