# ICOS Agent

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.2.0](https://img.shields.io/badge/AppVersion-0.2.0-informational?style=flat-square)

A Helm chart for the ICOS Agent

The ICOS Agent is responsible for managing the continuum (keeping track of the topology and availability of the current system) and the run-time (launching and monitoring the execution of services on-demand). Each ICOS Controller manages a set of Agents based on a proximity criteria; hence, ICOS Controllers are deployed on resource-rich computing facilities along the continuum to cover the whole geographical area.

This repository contains all the necessary information to install and deploy the ICOS Agent in a Kubernetes cluster.

## Requirements

| Repository | Name | Version |
|------------|------|---------|
|  | ocm-descriptor | 0.1.0 |
| oci://harbor.res.eng.it/icos-private/helm | nuvla-dm | ~0.0.1-main.10 |
| oci://harbor.res.eng.it/icos-private/helm | telemetruum-gateway | ~0.1.0-main.2 |

## Install Chart
This creates the release and instantiates all the Kubernetes components associated with the ICOS Agent.
```console
helm install [RELEASE_NAME] icos-agent
```

_See [values](#Values) below._

_See [helm install](https://helm.sh/docs/helm/helm_install/) for command documentation._

## Values

### Main

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| global.icos.agentId | string | `nil` | id of the agent |
| global.icos.controllerHost | string | `nil` | endpoint of the ICOS Controller |
| global.icos.iam.baseUrl | string | `"https://replace-with-keycloak-url"` | endpoint of the IAM service |
| global.icos.iam.publicKey | string | `"replace-with-realm-public-key"` | public key of the IAM service |
| global.icos.iam.realm | string | `"icos-realm"` | realm of the IAM service |
| global.icos.lighthouse.baseUrl | string | `"http://replace-with-light-house-url"` | endponint of the Lighthouse |

### OCM

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| global.icos.nuvlaDM.iamClientId | string | `"nuvla-dm-client-id"` | Deployment Manger clientId |
| global.icos.ocmDM.iamClientId | string | `"nuvla-dm-client-id"` | Deployment Manger clientId |
| ocm-descriptor.enabled | bool | `false` | Enable OCM Deployment Manager |

### Nuvla

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| global.icos.nuvlaDM.iamClientSecret | string | `"nuvla-dm-client-secret"` | Deployment Manger clientSecret |
| global.icos.nuvlaDM.nuvlaApiKey | string | `"nuvla-key"` | Nuvla apiKey |
| global.icos.nuvlaDM.nuvlaApiSecret | string | `"nuvla-secret"` | Nuvla apiSecret |
| global.icos.ocmDM.iamClientSecret | string | `"nuvla-dm-client-secret"` | Deployment Manger clientSecret |
| nuvla-dm.enabled | bool | `false` | Enable Nuvla Deployment Manager |

## Uninstall Chart
This removes all the Kubernetes components associated with the ICOS Agent and deletes the release.
```console
helm uninstall [RELEASE_NAME]
```
_See [helm uninstall](https://helm.sh/docs/helm/helm_uninstall/) for command documentation._

## Configuration
See [Customizing the Chart Before Installing](https://helm.sh/docs/intro/using_helm/#customizing-the-chart-before-installing). To see all configurable options with detailed comments, visit the chart's [values.yaml](./values.yaml), or run these configuration commands:

```console
helm show values icos-agent
```

You may similarly use the above configuration commands on each chart [dependency](#dependencies) to see its configurations.

# Legal
The ICOS Agent is released under the Apache 2.0 license.
Copyright © 2022-2024 ICOS. All rights reserved.

🇪🇺 This work has received funding from the European Union's HORIZON research and innovation programme under grant agreement No. 101070177.

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)