# Zarf Init Package for Longhorn

> :warning: EXPERIMENTAL!  This package is currently in an experimental state.

Zarf eliminates the [complexity of air gap software delivery](https://www.itopstimes.com/contain/air-gap-kubernetes-considerations-for-running-cloud-native-applications-without-the-cloud/) for Kubernetes clusters and cloud-native workloads using a declarative packaging strategy to support DevSecOps in offline and semi-connected environments.

## 👀 Looking for Zarf?

- [Zarf Website](https://zarf.dev)
- [Zarf Overview](https://docs.zarf.dev/docs/zarf-overview)
- [Zarf Repo](https://github.com/defenseunicorns/Zarf)

## Zarf Init Package for Longhorn

This repository contains the Zarf init package for Longhorn that creates a longhorn storage class on the cluster.

## Usage

### Prerequisites

- Zarf CLI (version >= `v0.62.0`)
    - <https://docs.zarf.dev/docs/getting-started>

- Connection to a host (or cluster) configured to run longhorn
    - <https://longhorn.io/docs/1.5.1/deploy/install/#installation-requirements>

## Quick Start

```bash
zarf package pull oci://ghcr.io/brandtkeller/zarf/zarf-init-longhorn/init:v0.62.0
```

```bash
zarf init --confirm
```

Once the init package is deployed, the Longhorn storage class will be created. The dashboard can be accessed via:

```bash
zarf connect longhorn-ui
```

### Create the Zarf init package

```bash
zarf package create . --set AGENT_IMAGE_TAG=$(zarf version)
```

### Initialize the Zarf init package

```bash
zarf init --confirm
```
> :warning: Different configuration options may be required depending on your environment

### Connecting an NFS backupstore
```yaml
defaultSettings:
  backupTarget: "nfs://192.168.0.10:/"
```