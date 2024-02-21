# sulfoxide-krypton

![Version: 1.1.0](https://img.shields.io/badge/Version-1.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.34.0](https://img.shields.io/badge/AppVersion-0.34.0-informational?style=flat-square)

Helm chart to deploy Karpenter to auto-scale EKS clusters

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| oci://public.ecr.aws/karpenter | karpenter | v0.34.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| al2 | object | `{"disruption":{"budgets":["20%"],"consolidateAfter":"30s","consolidationPolicy":"WhenUnderutilized","expireAfter":"720h"},"enable":false,"limits":{"cpu":50,"memory":"100Gi"},"requirements":[]}` | Values to control Amazon Linux 2 (AL2) provisioners |
| al2.disruption | object | `{"budgets":["20%"],"consolidateAfter":"30s","consolidationPolicy":"WhenUnderutilized","expireAfter":"720h"}` | Control how the provisioner handles disruptions |
| al2.disruption.budgets | list | `["20%"]` | Budgets to use for consolidating resources |
| al2.disruption.consolidateAfter | string | `"30s"` | Time to wait before consolidating resources |
| al2.disruption.consolidationPolicy | string | `"WhenUnderutilized"` | Consolidation policy to use |
| al2.disruption.expireAfter | string | `"720h"` | Time to wait before expiring resources (will automatically restart nodes periodically) |
| al2.enable | bool | `false` | Enable the AL2 Provisioner |
| al2.limits | object | `{"cpu":50,"memory":"100Gi"}` | Total limits that the provisioner can provision |
| al2.limits.cpu | int | `50` | Maximum CPU that the provisioner can provision |
| al2.limits.memory | string | `"100Gi"` | Maximum memory that the provisioner can provision |
| al2.requirements | list | `[]` | Requirement for the AL2 provisioner |
| bottlerocket | object | `{"disruption":{"budgets":["20%"],"consolidateAfter":"30s","consolidationPolicy":"WhenUnderutilized","expireAfter":"720h"},"enable":false,"limits":{"cpu":50,"memory":"100Gi"},"requirements":[]}` | Values to control Bottlerocket provisioners |
| bottlerocket.disruption | object | `{"budgets":["20%"],"consolidateAfter":"30s","consolidationPolicy":"WhenUnderutilized","expireAfter":"720h"}` | Control how the provisioner handles disruptions |
| bottlerocket.disruption.budgets | list | `["20%"]` | Budgets to use for consolidating resources |
| bottlerocket.disruption.consolidateAfter | string | `"30s"` | Time to wait before consolidating resources |
| bottlerocket.disruption.consolidationPolicy | string | `"WhenUnderutilized"` | Consolidation policy to use |
| bottlerocket.disruption.expireAfter | string | `"720h"` | Time to wait before expiring resources (will automatically restart nodes periodically) |
| bottlerocket.enable | bool | `false` | Enable the Bottlerocket Provisioner |
| bottlerocket.limits | object | `{"cpu":50,"memory":"100Gi"}` | Total limits that the provisioner can provision |
| bottlerocket.limits.cpu | int | `50` | Maximum CPU that the provisioner can provision |
| bottlerocket.limits.memory | string | `"100Gi"` | Maximum memory that the provisioner can provision |
| bottlerocket.requirements | list | `[]` | Requirement for the Bottlerocket provisioner |
| clusterName | string | `"name"` | Name of the cluster karpenter is deployed to |
| karpenter | object | `{"additionalAnnotations":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"krypton"}},"additionalLabels":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"krypton"}},"controller":{"resources":{"limits":{"cpu":"250m","memory":"0.5Gi"},"requests":{"cpu":"250m","memory":"0.5Gi"}}},"podAnnotations":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"krypton"},"atomi.cloud/module":"karpenter"},"podLabels":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"krypton"},"atomi.cloud/module":"karpenter"},"serviceAccount":{"annotations":{"eks.amazonaws.com/role-arn":"karpenter-controller-role"},"labels":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"krypton"}}},"serviceMonitor":{"enabled":false},"settings":{"clusterName":null,"interruptionQueueName":null},"topologySpreadConstraints":[{"labelSelector":{"matchLabels":{"<<":{"atomi.cloud/layer":"1","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"krypton"}}},"maxSkew":1,"topologyKey":"topology.kubernetes.io/zone","whenUnsatisfiable":"ScheduleAnyway"}]}` | Karpenter configuration. See [Karpenter Helm Chart](https://github.com/aws/karpenter-provider-aws/tree/main/charts/karpenter) |
| karpenterRole | string | `"karpenter-controller-role"` | Name of the karpenter role ARN that the karpenter controller has to assume |
| nodeRole | string | `"karpenter-role"` | Name of the node role that each node has to assume |
| serviceTree | object | `{"layer":"1","platform":"sulfoxide","service":"krypton"}` | AtomiCloud Service Tree. See [ServiceTree](https://atomicloud.larksuite.com/wiki/OkfJwTXGFiMJkrk6W3RuwRrZs64?theme=DARK&contentTheme=DARK#MHw5d76uDo2tBLx86cduFQMRsBb) |
| tags | object | `{"atomi.cloud/layer":"1","atomi.cloud/platform":"sulfoxide","atomi.cloud/service":"krypton"}` | Kubernetes labels and annotations, following Service Tree |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.1](https://github.com/norwoodj/helm-docs/releases/v1.11.1)