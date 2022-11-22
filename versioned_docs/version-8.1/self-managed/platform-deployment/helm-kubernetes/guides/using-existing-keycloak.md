---
id: using-existing-keycloak
title: "Using Existing Keycloak"
description: "Learn how to use an existing Keycloak instance in Camunda Platform 8 Self-Managed deployment."
---

Camunda Platform 8 Self-Managed has two different types of applications: Camunda applications (Operate, Optimize, Tasklist, etc.) and non-Camunda applications (such as Keycloak and Elasticsearch). For more details, review the [architecture](../../../platform-architecture/overview.md) documentation for more information on the different types of applications.

This guide steps through using an existing Keycloak instance, which is part of [Camunda Identity](../../../identity/what-is-identity.md). By default, [Helm chart deployment](../deploy.md) creates a new Keycloak instance, but it's possible to use an existing Keycloak instance either inside the same Kubernetes cluster or outside of it.

:::warning
Given Identity uses a Keycloak admin account, it could override the existing Keycloak configuration. Ensure you back up the Keycloak and test the deployment with a non-production environment first.
:::

## Preparation

Create a Kubernetes `Secret` with the existing Keycloak admin password. See an example of how to create this secret below:

```sh
kubectl create secret generic stage-keycloak \
    --from-literal=admin-password='<EXISTING_KEYCLOAK_ADMIN_PASSWORD>'
```

## Values file

The only change required to use the existing Keycloak is configuring the following values in the Camunda Platform 8 Self-Managed Helm chart:

```yaml
# File: existing-keycloak-values.yaml
global:
  identity:
    keycloak:
      url:
        # This will produce the following URL "https://keycloak.stage.svc.cluster.local:8443".
        # Also the host could be outside the Kubernetes cluster like "keycloak.stage.example.com".
        protocol: "https"
        host: "keycloak.stage.svc.cluster.local"
        port: "8443"
      auth:
        adminUser: "admin"
        existingSecret: "stage-keycloak"
        existingSecretKey: "admin-password"

identity:
  keycloak:
    enabled: false
```

Then, use the custom values file to [deploy Camunda Platform 8](../deploy.md) as usual.

```sh
helm install <RELEASE_NAME> camunda/camunda-platform -f existing-keycloak-values.yaml
```
