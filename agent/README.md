# agent

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v1.0.0](https://img.shields.io/badge/AppVersion-v1.0.0-informational?style=flat-square)

CRD and Agent for the Schwifty app

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| fullnameOverride | string | `""` |  |
| nameOverride | string | `""` |  |
| image.repository | string | `"69b10931.c1.gra9.container-registry.ovh.net/schwifty-public"` |  |
| image.name | string | `"agent"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.tag | string | `"v1.0.0"` |  |
| env | list | `[]` |  |
| serviceAccount | object | `{"annotations":{},"enabled":true,"name":"schwifty-back"}` | https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/ |
| podAnnotations.checksum/config | string | `"{{ toYaml $.Values.config | sha256sum }}"` |  |
| podSecurityContext | object | `{"fsGroup":1000}` | https://kubernetes.io/docs/tasks/configure-pod-container/security-context/ |
| securityContext | object | `{"capabilities":{"drop":["ALL"]},"runAsNonRoot":true,"runAsUser":1000}` | https://kubernetes.io/docs/tasks/configure-pod-container/security-context/ |
| service | object | `{"annotations":{},"ports":[{"name":"api","port":16666},{"name":"portforward","port":16667}],"type":"ClusterIP"}` | https://kubernetes.io/docs/concepts/services-networking/service/ |
| ingress | object | `{"className":"","enabled":false,"hosts":null}` | https://kubernetes.io/docs/concepts/services-networking/ingress/ |
| resources | object | `{}` | https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| replicaCount | int | `1` |  |
| autoscaling | object | `{"enabled":false,"maxReplicas":10,"minReplicas":2,"strategy":{"rollingUpdate":{"maxSurge":"10%","maxUnavailable":"10%"}},"targetCPUUtilizationPercentage":80}` | https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/ |
| podDisruptionBudget | object | `{"enabled":false,"maxUnavailable":"10%"}` | https://kubernetes.io/docs/tasks/run-application/configure-pdb/ |
| tolerations | list | `[]` |  |
| nodeSelector | object | `{}` |  |
| affinity | object | `{}` | https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes-using-node-affinity/ |
| topologySpreadConstraints | list | `[{"maxSkew":1,"topologyKey":"kubernetes.io/hostname","whenUnsatisfiable":"ScheduleAnyway"},{"maxSkew":1,"topologyKey":"topology.kubernetes.io/zone","whenUnsatisfiable":"ScheduleAnyway"}]` | https://kubernetes.io/docs/concepts/scheduling-eviction/topology-spread-constraints/ |
| livenessProbe | object | `{}` | https://kubernetes.io/fr/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/ |
| readinessProbe | object | `{}` | https://kubernetes.io/fr/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/ |
| startupProbe | object | `{}` | https://kubernetes.io/fr/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/ |
| rbac.enabled | bool | `true` |  |
| customizations.admin.groupSelector | string | `"schwifty-admin-users"` |  |
| customizations.admin.action | string | `"default"` |  |
| customizations.admin.navigation | string | `"admin"` |  |
| customizations.admin.listView | string | `"default"` |  |
| customizations.admin.getView | string | `"default"` |  |
| customizations.dev.groupSelector | string | `"schwifty-dev-users"` |  |
| customizations.dev.action | string | `"default"` |  |
| customizations.dev.navigation | string | `"dev"` |  |
| customizations.dev.listView | string | `"default"` |  |
| customizations.dev.getView | string | `"default"` |  |
| customizations.support.groupSelector | string | `"schwifty-support-users"` |  |
| customizations.support.action | string | `"default"` |  |
| customizations.support.navigation | string | `"support"` |  |
| customizations.support.listView | string | `"default"` |  |
| customizations.support.getView | string | `"default"` |  |
| actions.default[0].type | string | `"grafana"` |  |
| actions.default[0].include[0] | string | `"pods"` |  |
| actions.default[0].exclude | list | `[]` |  |
| actions.default[0].verb | string | `"link"` |  |
| actions.default[0].title | string | `"Monitoring"` |  |
| actions.default[0].icon | string | `"https://upload.wikimedia.org/wikipedia/commons/3/3b/Grafana_icon.svg"` |  |
| actions.default[0].payloadTemplate | string | `"https://grafana.schwifty.fr/d/Schwifty/pods?orgId=1&var-namespace={{$.metadata.namespace}}&var-pod={{$.metadata.name}}"` |  |
| actions.default[0].parameters | list | `[]` |  |
| actions.default[1].type | string | `"cordon"` |  |
| actions.default[1].include[0] | string | `"nodes"` |  |
| actions.default[1].exclude[0] | string | `"*"` |  |
| actions.default[2].type | string | `"uncordon"` |  |
| actions.default[2].include[0] | string | `"nodes"` |  |
| actions.default[2].exclude[0] | string | `"*"` |  |
| actions.default[3].type | string | `"drain"` |  |
| actions.default[3].include[0] | string | `"nodes"` |  |
| actions.default[3].exclude[0] | string | `"*"` |  |
| actions.default[4].type | string | `"exec"` |  |
| actions.default[4].include | list | `[]` |  |
| actions.default[4].exclude[0] | string | `"*"` |  |
| actions.default[5].type | string | `"logs"` |  |
| actions.default[5].include[0] | string | `"pods"` |  |
| actions.default[5].exclude[0] | string | `"*"` |  |
| actions.default[6].type | string | `"portforward"` |  |
| actions.default[6].include[0] | string | `"pods"` |  |
| actions.default[6].exclude[0] | string | `"*"` |  |
| actions.default[7].type | string | `"restart"` |  |
| actions.default[7].include[0] | string | `"apps/deployments"` |  |
| actions.default[7].include[1] | string | `"apps/statefulsets"` |  |
| actions.default[7].include[2] | string | `"apps/daemonset"` |  |
| actions.default[7].exclude[0] | string | `"*"` |  |
| actions.default[7].verb | string | `"patch"` |  |
| actions.default[7].title | string | `"Restart"` |  |
| actions.default[7].icon | string | `"58927"` |  |
| actions.default[7].payloadTemplate | string | `"{\n  \"spec\": {\n    \"template\": {\n      \"metadata\": {\n        \"annotations\": {\n          \"schwifty.pewty.fr/update\": \"{{datenow}}\"\n        }\n      }\n    }\n  }\n}\n"` |  |
| actions.default[7].parameters | list | `[]` |  |
| actions.default[8].type | string | `"scale"` |  |
| actions.default[8].include[0] | string | `"apps/deployments"` |  |
| actions.default[8].include[1] | string | `"apps/statefulsets"` |  |
| actions.default[8].include[2] | string | `"apps/replicasets"` |  |
| actions.default[8].exclude[0] | string | `"*"` |  |
| actions.default[8].verb | string | `"patch"` |  |
| actions.default[8].title | string | `"Scale"` |  |
| actions.default[8].icon | string | `"62475"` |  |
| actions.default[8].payloadTemplate | string | `"{\n  \"spec\": {\n    \"replicas\": {{replicas}}\n  }\n}\n"` |  |
| actions.default[8].parameters[0].name | string | `"replicas"` |  |
| actions.default[8].parameters[0].defaultValue | string | `"1"` |  |
| actions.default[8].parameters[0].description | string | `"Number of replicas"` |  |
| actions.default[9].type | string | `"sync"` |  |
| actions.default[9].include[0] | string | `"helm.toolkit.fluxcd.io/helmreleases"` |  |
| actions.default[9].include[1] | string | `"kustomize.toolkit.fluxcd.io/kustomizations"` |  |
| actions.default[9].include[2] | string | `"source.toolkit.fluxcd.io/gitrepositories"` |  |
| actions.default[9].include[3] | string | `"external-secrets.io/externalsecrets"` |  |
| actions.default[9].include[4] | string | `"external-secrets.io/pushsecrets"` |  |
| actions.default[9].exclude[0] | string | `"*"` |  |
| actions.default[9].verb | string | `"patch"` |  |
| actions.default[9].title | string | `"Sync"` |  |
| actions.default[9].icon | string | `"58927"` |  |
| actions.default[9].payloadTemplate | string | `"{\n  \"metadata\": {\n    \"annotations\": {\n      \"schwifty.pewty.fr/update\": \"{{datenow}}\"\n    }\n  }\n}\n"` |  |
| actions.default[9].parameters | list | `[]` |  |
| actions.default[10].type | string | `"pause"` |  |
| actions.default[10].include[0] | string | `"helm.toolkit.fluxcd.io/helmreleases"` |  |
| actions.default[10].include[1] | string | `"kustomize.toolkit.fluxcd.io/kustomizations"` |  |
| actions.default[10].include[2] | string | `"source.toolkit.fluxcd.io/gitrepositories"` |  |
| actions.default[10].exclude[0] | string | `"*"` |  |
| actions.default[10].verb | string | `"patch"` |  |
| actions.default[10].title | string | `"Pause"` |  |
| actions.default[10].icon | string | `"58492"` |  |
| actions.default[10].payloadTemplate | string | `"{\n  \"spec\": {\n    \"suspend\": true\n  }\n}\n"` |  |
| actions.default[10].parameters | list | `[]` |  |
| actions.default[11].type | string | `"resume"` |  |
| actions.default[11].include[0] | string | `"helm.toolkit.fluxcd.io/helmreleases"` |  |
| actions.default[11].include[1] | string | `"kustomize.toolkit.fluxcd.io/kustomizations"` |  |
| actions.default[11].include[2] | string | `"source.toolkit.fluxcd.io/gitrepositories"` |  |
| actions.default[11].exclude[0] | string | `"*"` |  |
| actions.default[11].verb | string | `"patch"` |  |
| actions.default[11].title | string | `"Resume"` |  |
| actions.default[11].icon | string | `"58573"` |  |
| actions.default[11].payloadTemplate | string | `"{\n  \"spec\": {\n    \"suspend\": false\n  }\n}\n"` |  |
| actions.default[11].parameters | list | `[]` |  |
| actions.default[12].type | string | `"get"` |  |
| actions.default[12].include[0] | string | `"*"` |  |
| actions.default[12].exclude | list | `[]` |  |
| actions.default[13].type | string | `"create"` |  |
| actions.default[13].include[0] | string | `"*"` |  |
| actions.default[13].exclude | list | `[]` |  |
| actions.default[14].type | string | `"edit"` |  |
| actions.default[14].include[0] | string | `"*"` |  |
| actions.default[14].exclude | list | `[]` |  |
| actions.default[15].type | string | `"delete"` |  |
| actions.default[15].include[0] | string | `"*"` |  |
| actions.default[15].exclude | list | `[]` |  |
| navigations.admin.other.enabled | bool | `true` |  |
| navigations.admin.other.label | string | `"Other"` |  |
| navigations.admin.other.icon | string | `"62020"` |  |
| navigations.admin.items[0].label | string | `"Nodes"` |  |
| navigations.admin.items[0].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/infrastructure_components/unlabeled/node.svg"` |  |
| navigations.admin.items[0].items[0].label | string | `"NodeClaims"` |  |
| navigations.admin.items[0].items[0].route | string | `"karpenter.sh/nodeclaims"` |  |
| navigations.admin.items[0].items[1].label | string | `"Nodes"` |  |
| navigations.admin.items[0].items[1].route | string | `"nodes"` |  |
| navigations.admin.items[0].items[2].label | string | `"NodePools"` |  |
| navigations.admin.items[0].items[2].route | string | `"karpenter.sh/nodepools"` |  |
| navigations.admin.items[0].items[3].label | string | `"EC2NodeClass"` |  |
| navigations.admin.items[0].items[3].route | string | `"karpenter.k8s.aws/ec2nodeclasses"` |  |
| navigations.admin.items[1].label | string | `"Workload"` |  |
| navigations.admin.items[1].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/pod.svg"` |  |
| navigations.admin.items[1].items[0].label | string | `"Pods"` |  |
| navigations.admin.items[1].items[0].route | string | `"pods"` |  |
| navigations.admin.items[1].items[1].label | string | `"Deployments"` |  |
| navigations.admin.items[1].items[1].route | string | `"apps/deployments"` |  |
| navigations.admin.items[1].items[2].label | string | `"StatefulSets"` |  |
| navigations.admin.items[1].items[2].route | string | `"apps/statefulsets"` |  |
| navigations.admin.items[1].items[3].label | string | `"DaemonSets"` |  |
| navigations.admin.items[1].items[3].route | string | `"apps/daemonsets"` |  |
| navigations.admin.items[1].items[4].label | string | `"ReplicaSets"` |  |
| navigations.admin.items[1].items[4].route | string | `"apps/replicasets"` |  |
| navigations.admin.items[1].items[5].label | string | `"ReplicationController"` |  |
| navigations.admin.items[1].items[5].route | string | `"replicationcontrollers"` |  |
| navigations.admin.items[1].items[6].label | string | `"Jobs"` |  |
| navigations.admin.items[1].items[6].route | string | `"batch/jobs"` |  |
| navigations.admin.items[1].items[7].label | string | `"CronJobs"` |  |
| navigations.admin.items[1].items[7].route | string | `"batch/cronjobs"` |  |
| navigations.admin.items[2].label | string | `"Config"` |  |
| navigations.admin.items[2].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/cm.svg"` |  |
| navigations.admin.items[2].items[0].label | string | `"ConfigMaps"` |  |
| navigations.admin.items[2].items[0].route | string | `"configmaps"` |  |
| navigations.admin.items[2].items[1].label | string | `"Secrets"` |  |
| navigations.admin.items[2].items[1].route | string | `"secrets"` |  |
| navigations.admin.items[2].items[2].label | string | `"ResourceQuotas"` |  |
| navigations.admin.items[2].items[2].route | string | `"resourcequotas"` |  |
| navigations.admin.items[2].items[3].label | string | `"LimitRanges"` |  |
| navigations.admin.items[2].items[3].route | string | `"limitranges"` |  |
| navigations.admin.items[2].items[4].label | string | `"HorizontalPodAutoscalers"` |  |
| navigations.admin.items[2].items[4].route | string | `"autoscaling/horizontalpodautoscalers"` |  |
| navigations.admin.items[2].items[5].label | string | `"PodDisruptionBudgets"` |  |
| navigations.admin.items[2].items[5].route | string | `"policy/poddisruptionbudgets"` |  |
| navigations.admin.items[2].items[6].label | string | `"PriorityClasses"` |  |
| navigations.admin.items[2].items[6].route | string | `"scheduling.k8s.io/priorityclasses"` |  |
| navigations.admin.items[2].items[7].label | string | `"RuntimeClasses"` |  |
| navigations.admin.items[2].items[7].route | string | `"node.k8s.io/runtimeclasses"` |  |
| navigations.admin.items[2].items[8].label | string | `"Lease"` |  |
| navigations.admin.items[2].items[8].route | string | `"coordination.k8s.io/leases"` |  |
| navigations.admin.items[2].items[9].label | string | `"MutatingWebhookConfigurations"` |  |
| navigations.admin.items[2].items[9].route | string | `"admissionregistration.k8s.io/mutatingwebhookconfigurations"` |  |
| navigations.admin.items[2].items[10].label | string | `"ValidatingWebhookConfigurations"` |  |
| navigations.admin.items[2].items[10].route | string | `"admissionregistration.k8s.io/validatingwebhookconfigurations"` |  |
| navigations.admin.items[2].items[11].label | string | `"CustomResourceDefinitions"` |  |
| navigations.admin.items[2].items[11].route | string | `"apiextensions.k8s.io/customresourcedefinitions"` |  |
| navigations.admin.items[2].items[12].label | string | `"PodSecurityPolicies"` |  |
| navigations.admin.items[2].items[12].route | string | `"policy/podsecuritypolicies"` |  |
| navigations.admin.items[3].label | string | `"Network"` |  |
| navigations.admin.items[3].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/svc.svg"` |  |
| navigations.admin.items[3].items[0].label | string | `"Services"` |  |
| navigations.admin.items[3].items[0].route | string | `"services"` |  |
| navigations.admin.items[3].items[1].label | string | `"Endpoints"` |  |
| navigations.admin.items[3].items[1].route | string | `"endpoints"` |  |
| navigations.admin.items[3].items[2].label | string | `"Ingresses"` |  |
| navigations.admin.items[3].items[2].route | string | `"networking.k8s.io/ingresses"` |  |
| navigations.admin.items[3].items[3].label | string | `"IngresClasses"` |  |
| navigations.admin.items[3].items[3].route | string | `"networking.k8s.io/ingressclasses"` |  |
| navigations.admin.items[4].label | string | `"Storage"` |  |
| navigations.admin.items[4].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/pvc.svg"` |  |
| navigations.admin.items[4].items[0].label | string | `"PersistentVolumeClaims"` |  |
| navigations.admin.items[4].items[0].route | string | `"persistentvolumeclaims"` |  |
| navigations.admin.items[4].items[1].label | string | `"PersistentVolumes"` |  |
| navigations.admin.items[4].items[1].route | string | `"persistentvolumes"` |  |
| navigations.admin.items[4].items[2].label | string | `"StorageClasses"` |  |
| navigations.admin.items[4].items[2].route | string | `"storage.k8s.io/storageclasses"` |  |
| navigations.admin.items[5].label | string | `"Access Control"` |  |
| navigations.admin.items[5].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/sa.svg"` |  |
| navigations.admin.items[5].items[0].label | string | `"ServiceAccounts"` |  |
| navigations.admin.items[5].items[0].route | string | `"serviceaccounts"` |  |
| navigations.admin.items[5].items[1].label | string | `"Roles"` |  |
| navigations.admin.items[5].items[1].route | string | `"rbac.authorization.k8s.io/roles"` |  |
| navigations.admin.items[5].items[2].label | string | `"RoleBindings"` |  |
| navigations.admin.items[5].items[2].route | string | `"rbac.authorization.k8s.io/rolebindings"` |  |
| navigations.admin.items[5].items[3].label | string | `"ClusterRoles"` |  |
| navigations.admin.items[5].items[3].route | string | `"rbac.authorization.k8s.io/clusterroles"` |  |
| navigations.admin.items[5].items[4].label | string | `"ClusterRoleBindings"` |  |
| navigations.admin.items[5].items[4].route | string | `"rbac.authorization.k8s.io/clusterrolebindings"` |  |
| navigations.admin.items[6].label | string | `"FluxCD"` |  |
| navigations.admin.items[6].icon | string | `"https://raw.githubusercontent.com/fluxcd/website/refs/heads/main/assets/icons/logo.svg"` |  |
| navigations.admin.items[6].items[0].label | string | `"HelmReleases"` |  |
| navigations.admin.items[6].items[0].route | string | `"helm.toolkit.fluxcd.io/helmreleases"` |  |
| navigations.admin.items[6].items[1].label | string | `"HelmCharts"` |  |
| navigations.admin.items[6].items[1].route | string | `"source.toolkit.fluxcd.io/helmcharts"` |  |
| navigations.admin.items[6].items[2].label | string | `"HelmRepositories"` |  |
| navigations.admin.items[6].items[2].route | string | `"source.toolkit.fluxcd.io/helmrepositories"` |  |
| navigations.admin.items[6].items[3].label | string | `"Kustomizations"` |  |
| navigations.admin.items[6].items[3].route | string | `"kustomize.toolkit.fluxcd.io/kustomizations"` |  |
| navigations.admin.items[6].items[4].label | string | `"GitRepositories"` |  |
| navigations.admin.items[6].items[4].route | string | `"source.toolkit.fluxcd.io/gitrepositories"` |  |
| navigations.admin.items[7].label | string | `"External Secrets"` |  |
| navigations.admin.items[7].icon | string | `"984363"` |  |
| navigations.admin.items[7].items[0].label | string | `"External Secrets"` |  |
| navigations.admin.items[7].items[0].route | string | `"external-secrets.io/externalsecrets"` |  |
| navigations.admin.items[7].items[1].label | string | `"Cluster External Secrets"` |  |
| navigations.admin.items[7].items[1].route | string | `"external-secrets.io/clusterexternalsecrets"` |  |
| navigations.admin.items[7].items[2].label | string | `"Push Secrets"` |  |
| navigations.admin.items[7].items[2].route | string | `"external-secrets.io/pushsecrets"` |  |
| navigations.admin.items[7].items[3].label | string | `"Secret Stores"` |  |
| navigations.admin.items[7].items[3].route | string | `"external-secrets.io/secretstores"` |  |
| navigations.admin.items[7].items[4].label | string | `"Cluster Secret Stores"` |  |
| navigations.admin.items[7].items[4].route | string | `"external-secrets.io/clustersecretstores"` |  |
| navigations.admin.items[8].label | string | `"Homer"` |  |
| navigations.admin.items[8].icon | string | `"https://raw.githubusercontent.com/bastienwirtz/homer/refs/heads/main/public/assets/icons/logo.svg"` |  |
| navigations.admin.items[8].items[0].label | string | `"Homer Services"` |  |
| navigations.admin.items[8].items[0].route | string | `"homer.bananaops.io/homerservices"` |  |
| navigations.admin.items[9].label | string | `"Velero"` |  |
| navigations.admin.items[9].icon | string | `"58704"` |  |
| navigations.admin.items[9].items[0].label | string | `"Schedules"` |  |
| navigations.admin.items[9].items[0].route | string | `"velero.io/schedules"` |  |
| navigations.admin.items[9].items[1].label | string | `"Backups"` |  |
| navigations.admin.items[9].items[1].route | string | `"velero.io/backups"` |  |
| navigations.admin.items[10].label | string | `"Chaos Mesh"` |  |
| navigations.admin.items[10].icon | string | `"https://raw.githubusercontent.com/chaos-mesh/chaos-mesh/refs/heads/master/ui/app/src/images/logo-mini.svg"` |  |
| navigations.admin.items[10].items[0].label | string | `"Physical Machines"` |  |
| navigations.admin.items[10].items[0].route | string | `"chaos-mesh.org/physicalmachines"` |  |
| navigations.admin.items[10].items[1].label | string | `"AWS Chaos"` |  |
| navigations.admin.items[10].items[1].route | string | `"chaos-mesh.org/awschaos"` |  |
| navigations.admin.items[10].items[2].label | string | `"Network Chaos"` |  |
| navigations.admin.items[10].items[2].route | string | `"chaos-mesh.org/networkchaos"` |  |
| navigations.admin.items[10].items[3].label | string | `"Status Checks"` |  |
| navigations.admin.items[10].items[3].route | string | `"chaos-mesh.org/statuschecks"` |  |
| navigations.admin.items[10].items[4].label | string | `"Kernel Chaos"` |  |
| navigations.admin.items[10].items[4].route | string | `"chaos-mesh.org/kernelchaos"` |  |
| navigations.admin.items[10].items[5].label | string | `"JVM Chaos"` |  |
| navigations.admin.items[10].items[5].route | string | `"chaos-mesh.org/jvmchaos"` |  |
| navigations.admin.items[10].items[6].label | string | `"Workflow Nodes"` |  |
| navigations.admin.items[10].items[6].route | string | `"chaos-mesh.org/workflownodes"` |  |
| navigations.admin.items[10].items[7].label | string | `"I/O Chaos"` |  |
| navigations.admin.items[10].items[7].route | string | `"chaos-mesh.org/iochaos"` |  |
| navigations.admin.items[10].items[8].label | string | `"Pod I/O Chaos"` |  |
| navigations.admin.items[10].items[8].route | string | `"chaos-mesh.org/podiochaos"` |  |
| navigations.admin.items[10].items[9].label | string | `"Pod Network Chaos"` |  |
| navigations.admin.items[10].items[9].route | string | `"chaos-mesh.org/podnetworkchaos"` |  |
| navigations.admin.items[10].items[10].label | string | `"Physical Machine Chaos"` |  |
| navigations.admin.items[10].items[10].route | string | `"chaos-mesh.org/physicalmachinechaos"` |  |
| navigations.admin.items[10].items[11].label | string | `"HTTP Chaos"` |  |
| navigations.admin.items[10].items[11].route | string | `"chaos-mesh.org/httpchaos"` |  |
| navigations.admin.items[10].items[12].label | string | `"Time Chaos"` |  |
| navigations.admin.items[10].items[12].route | string | `"chaos-mesh.org/timechaos"` |  |
| navigations.admin.items[10].items[13].label | string | `"Stress Chaos"` |  |
| navigations.admin.items[10].items[13].route | string | `"chaos-mesh.org/stresschaos"` |  |
| navigations.admin.items[10].items[14].label | string | `"DNS Chaos"` |  |
| navigations.admin.items[10].items[14].route | string | `"chaos-mesh.org/dnschaos"` |  |
| navigations.admin.items[10].items[15].label | string | `"Pod HTTP Chaos"` |  |
| navigations.admin.items[10].items[15].route | string | `"chaos-mesh.org/podhttpchaos"` |  |
| navigations.admin.items[10].items[16].label | string | `"Workflows"` |  |
| navigations.admin.items[10].items[16].route | string | `"chaos-mesh.org/workflows"` |  |
| navigations.admin.items[10].items[17].label | string | `"Block Chaos"` |  |
| navigations.admin.items[10].items[17].route | string | `"chaos-mesh.org/blockchaos"` |  |
| navigations.admin.items[10].items[18].label | string | `"Schedules"` |  |
| navigations.admin.items[10].items[18].route | string | `"chaos-mesh.org/schedules"` |  |
| navigations.admin.items[11].label | string | `"Namespace"` |  |
| navigations.admin.items[11].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/ns.svg"` |  |
| navigations.admin.items[11].route | string | `"namespaces"` |  |
| navigations.admin.items[12].label | string | `"Event"` |  |
| navigations.admin.items[12].icon | string | `"57918"` |  |
| navigations.admin.items[12].route | string | `"events"` |  |
| navigations.admin.items[13].label | string | `"Customization"` |  |
| navigations.admin.items[13].icon | string | `"57778"` |  |
| navigations.admin.items[13].items[0].label | string | `"Customization"` |  |
| navigations.admin.items[13].items[0].route | string | `"schwifty.pewty.fr/customizations"` |  |
| navigations.admin.items[13].items[1].label | string | `"GetView"` |  |
| navigations.admin.items[13].items[1].route | string | `"schwifty.pewty.fr/getviews"` |  |
| navigations.admin.items[13].items[2].label | string | `"Action"` |  |
| navigations.admin.items[13].items[2].route | string | `"schwifty.pewty.fr/actions"` |  |
| navigations.admin.items[13].items[3].label | string | `"Navigation"` |  |
| navigations.admin.items[13].items[3].route | string | `"schwifty.pewty.fr/navigations"` |  |
| navigations.admin.items[13].items[4].label | string | `"ListView"` |  |
| navigations.admin.items[13].items[4].route | string | `"schwifty.pewty.fr/listviews"` |  |
| navigations.dev.other.enabled | bool | `false` |  |
| navigations.dev.items[0].label | string | `"Workload"` |  |
| navigations.dev.items[0].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/pod.svg"` |  |
| navigations.dev.items[0].items[0].label | string | `"Pods"` |  |
| navigations.dev.items[0].items[0].route | string | `"pods"` |  |
| navigations.dev.items[0].items[1].label | string | `"Deployments"` |  |
| navigations.dev.items[0].items[1].route | string | `"apps/deployments"` |  |
| navigations.dev.items[0].items[2].label | string | `"StatefulSets"` |  |
| navigations.dev.items[0].items[2].route | string | `"apps/statefulsets"` |  |
| navigations.dev.items[0].items[3].label | string | `"DaemonSets"` |  |
| navigations.dev.items[0].items[3].route | string | `"apps/daemonsets"` |  |
| navigations.dev.items[0].items[4].label | string | `"ReplicaSets"` |  |
| navigations.dev.items[0].items[4].route | string | `"apps/replicasets"` |  |
| navigations.dev.items[0].items[5].label | string | `"ReplicationController"` |  |
| navigations.dev.items[0].items[5].route | string | `"replicationcontrollers"` |  |
| navigations.dev.items[0].items[6].label | string | `"Jobs"` |  |
| navigations.dev.items[0].items[6].route | string | `"batch/jobs"` |  |
| navigations.dev.items[0].items[7].label | string | `"CronJobs"` |  |
| navigations.dev.items[0].items[7].route | string | `"batch/cronjobs"` |  |
| navigations.dev.items[1].label | string | `"Config"` |  |
| navigations.dev.items[1].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/cm.svg"` |  |
| navigations.dev.items[1].items[0].label | string | `"ConfigMaps"` |  |
| navigations.dev.items[1].items[0].route | string | `"configmaps"` |  |
| navigations.dev.items[1].items[1].label | string | `"Secrets"` |  |
| navigations.dev.items[1].items[1].route | string | `"secrets"` |  |
| navigations.dev.items[1].items[2].label | string | `"ResourceQuotas"` |  |
| navigations.dev.items[1].items[2].route | string | `"resourcequotas"` |  |
| navigations.dev.items[1].items[3].label | string | `"LimitRanges"` |  |
| navigations.dev.items[1].items[3].route | string | `"limitranges"` |  |
| navigations.dev.items[1].items[4].label | string | `"HorizontalPodAutoscalers"` |  |
| navigations.dev.items[1].items[4].route | string | `"autoscaling/horizontalpodautoscalers"` |  |
| navigations.dev.items[1].items[5].label | string | `"PodDisruptionBudgets"` |  |
| navigations.dev.items[1].items[5].route | string | `"policy/poddisruptionbudgets"` |  |
| navigations.dev.items[2].label | string | `"Network"` |  |
| navigations.dev.items[2].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/svc.svg"` |  |
| navigations.dev.items[2].items[0].label | string | `"Services"` |  |
| navigations.dev.items[2].items[0].route | string | `"services"` |  |
| navigations.dev.items[2].items[1].label | string | `"Ingresses"` |  |
| navigations.dev.items[2].items[1].route | string | `"networking.k8s.io/ingresses"` |  |
| navigations.dev.items[3].label | string | `"Storage"` |  |
| navigations.dev.items[3].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/pvc.svg"` |  |
| navigations.dev.items[3].items[0].label | string | `"PersistentVolumeClaims"` |  |
| navigations.dev.items[3].items[0].route | string | `"persistentvolumeclaims"` |  |
| navigations.dev.items[3].items[1].label | string | `"PersistentVolumes"` |  |
| navigations.dev.items[3].items[1].route | string | `"persistentvolumes"` |  |
| navigations.dev.items[4].label | string | `"FluxCD"` |  |
| navigations.dev.items[4].icon | string | `"https://raw.githubusercontent.com/fluxcd/website/refs/heads/main/assets/icons/logo.svg"` |  |
| navigations.dev.items[4].items[0].label | string | `"HelmReleases"` |  |
| navigations.dev.items[4].items[0].route | string | `"helm.toolkit.fluxcd.io/helmreleases"` |  |
| navigations.dev.items[4].items[1].label | string | `"Kustomizations"` |  |
| navigations.dev.items[4].items[1].route | string | `"kustomize.toolkit.fluxcd.io/kustomizations"` |  |
| navigations.dev.items[5].label | string | `"External Secrets"` |  |
| navigations.dev.items[5].icon | string | `"https://raw.githubusercontent.com/external-secrets/external-secrets/refs/heads/main/docs/pictures/eso-round-logo.svg"` |  |
| navigations.dev.items[5].items[0].label | string | `"External Secrets"` |  |
| navigations.dev.items[5].items[0].route | string | `"external-secrets.io/externalsecrets"` |  |
| navigations.dev.items[5].items[1].label | string | `"Push Secrets"` |  |
| navigations.dev.items[5].items[1].route | string | `"external-secrets.io/pushsecrets"` |  |
| navigations.dev.items[6].label | string | `"Homer"` |  |
| navigations.dev.items[6].icon | string | `"https://raw.githubusercontent.com/bastienwirtz/homer/refs/heads/main/public/assets/icons/logo.svg"` |  |
| navigations.dev.items[6].items[0].label | string | `"Homer Services"` |  |
| navigations.dev.items[6].items[0].route | string | `"homer.bananaops.io/homerservices"` |  |
| navigations.dev.items[7].label | string | `"Event"` |  |
| navigations.dev.items[7].icon | string | `"57918"` |  |
| navigations.dev.items[7].route | string | `"events"` |  |
| navigations.support.other.enabled | bool | `false` |  |
| navigations.support.items[0].label | string | `"Workload"` |  |
| navigations.support.items[0].icon | string | `"https://raw.githubusercontent.com/kubernetes/community/refs/heads/master/icons/svg/resources/unlabeled/pod.svg"` |  |
| navigations.support.items[0].items[0].label | string | `"Pods"` |  |
| navigations.support.items[0].items[0].route | string | `"pods"` |  |
| navigations.support.items[0].items[1].label | string | `"Deployments"` |  |
| navigations.support.items[0].items[1].route | string | `"apps/deployments"` |  |
| navigations.support.items[0].items[2].label | string | `"StatefulSets"` |  |
| navigations.support.items[0].items[2].route | string | `"apps/statefulsets"` |  |
| navigations.support.items[0].items[3].label | string | `"DaemonSets"` |  |
| navigations.support.items[0].items[3].route | string | `"apps/daemonsets"` |  |
| navigations.support.items[1].label | string | `"FluxCD"` |  |
| navigations.support.items[1].icon | string | `"https://raw.githubusercontent.com/fluxcd/website/refs/heads/main/assets/icons/logo.svg"` |  |
| navigations.support.items[1].items[0].label | string | `"HelmReleases"` |  |
| navigations.support.items[1].items[0].route | string | `"helm.toolkit.fluxcd.io/helmreleases"` |  |
| navigations.support.items[2].label | string | `"Event"` |  |
| navigations.support.items[2].icon | string | `"57918"` |  |
| navigations.support.items[2].route | string | `"events"` |  |
| listViews.default[0].include[0] | string | `"nodes"` |  |
| listViews.default[0].exclude[0] | string | `"*"` |  |
| listViews.default[0].items[0].label | string | `"Name"` |  |
| listViews.default[0].items[0].key | string | `"$.metadata.name"` |  |
| listViews.default[0].items[0].width | int | `3` |  |
| listViews.default[0].items[1].label | string | `"Ready"` |  |
| listViews.default[0].items[1].key | string | `"$.status.conditions[?(@.type==\"Ready\")].status"` |  |
| listViews.default[0].items[2].label | string | `"Age"` |  |
| listViews.default[0].items[2].key | string | `"$.metadata.creationTimestamp"` |  |
| listViews.default[0].items[2].type | string | `"duration"` |  |
| listViews.default[0].items[3].label | string | `"Version"` |  |
| listViews.default[0].items[3].key | string | `"$.status.nodeInfo.kubeletVersion"` |  |
| listViews.default[0].items[3].width | int | `2` |  |
| listViews.default[1].include[0] | string | `"pods"` |  |
| listViews.default[1].exclude[0] | string | `"*"` |  |
| listViews.default[1].items[0].label | string | `"Name"` |  |
| listViews.default[1].items[0].key | string | `"$.metadata.name"` |  |
| listViews.default[1].items[0].width | int | `4` |  |
| listViews.default[1].items[1].label | string | `"Status"` |  |
| listViews.default[1].items[1].key | string | `"$.status.phase"` |  |
| listViews.default[1].items[1].type | string | `"badge"` |  |
| listViews.default[1].items[1].width | int | `1` |  |
| listViews.default[1].items[2].label | string | `"Age"` |  |
| listViews.default[1].items[2].key | string | `"$.metadata.creationTimestamp"` |  |
| listViews.default[1].items[2].type | string | `"duration"` |  |
| listViews.default[1].items[3].label | string | `"Node"` |  |
| listViews.default[1].items[3].key | string | `"$.spec.nodeName"` |  |
| listViews.default[1].items[3].width | int | `5` |  |
| listViews.default[1].items[4].label | string | `"Namespace"` |  |
| listViews.default[1].items[4].key | string | `"$.metadata.namespace"` |  |
| listViews.default[1].items[4].width | int | `3` |  |
| listViews.default[2].include[0] | string | `"apps/deployments"` |  |
| listViews.default[2].exclude[0] | string | `"*"` |  |
| listViews.default[2].items[0].label | string | `"Name"` |  |
| listViews.default[2].items[0].key | string | `"$.metadata.name"` |  |
| listViews.default[2].items[0].width | int | `4` |  |
| listViews.default[2].items[1].label | string | `"Current"` |  |
| listViews.default[2].items[1].key | string | `"$.status.replicas"` |  |
| listViews.default[2].items[2].label | string | `"Desired"` |  |
| listViews.default[2].items[2].key | string | `"$.spec.replicas"` |  |
| listViews.default[2].items[3].label | string | `"Age"` |  |
| listViews.default[2].items[3].key | string | `"$.metadata.creationTimestamp"` |  |
| listViews.default[2].items[3].type | string | `"duration"` |  |
| listViews.default[3].include[0] | string | `"helm.toolkit.fluxcd.io/helmreleases"` |  |
| listViews.default[3].exclude[0] | string | `"*"` |  |
| listViews.default[3].items[0].label | string | `"Name"` |  |
| listViews.default[3].items[0].key | string | `"$.metadata.name"` |  |
| listViews.default[3].items[0].width | int | `4` |  |
| listViews.default[3].items[1].label | string | `"Age"` |  |
| listViews.default[3].items[1].key | string | `"$.metadata.creationTimestamp"` |  |
| listViews.default[3].items[1].type | string | `"duration"` |  |
| listViews.default[3].items[2].label | string | `"Ready"` |  |
| listViews.default[3].items[2].key | string | `"$.status.conditions[?(@.type==\"Ready\")].status"` |  |
| listViews.default[4].include[0] | string | `"source.toolkit.fluxcd.io/helmcharts"` |  |
| listViews.default[4].exclude[0] | string | `"*"` |  |
| listViews.default[4].items[0].label | string | `"Name"` |  |
| listViews.default[4].items[0].key | string | `"$.metadata.name"` |  |
| listViews.default[4].items[0].width | int | `4` |  |
| listViews.default[4].items[1].label | string | `"Chart"` |  |
| listViews.default[4].items[1].key | string | `"$.spec.chart"` |  |
| listViews.default[4].items[1].width | int | `3` |  |
| listViews.default[4].items[2].label | string | `"Version"` |  |
| listViews.default[4].items[2].key | string | `"$.spec.version"` |  |
| listViews.default[4].items[3].label | string | `"Age"` |  |
| listViews.default[4].items[3].key | string | `"$.metadata.creationTimestamp"` |  |
| listViews.default[4].items[3].type | string | `"duration"` |  |
| listViews.default[4].items[4].label | string | `"Ready"` |  |
| listViews.default[4].items[4].key | string | `"$.status.conditions[?(@.type==\"Ready\")].status"` |  |
| listViews.default[5].include[0] | string | `"source.toolkit.fluxcd.io/helmrepositories"` |  |
| listViews.default[5].exclude[0] | string | `"*"` |  |
| listViews.default[5].items[0].label | string | `"Name"` |  |
| listViews.default[5].items[0].key | string | `"$.metadata.name"` |  |
| listViews.default[5].items[0].width | int | `2` |  |
| listViews.default[5].items[1].label | string | `"URL"` |  |
| listViews.default[5].items[1].key | string | `"$.spec.url"` |  |
| listViews.default[5].items[1].width | int | `4` |  |
| listViews.default[5].items[2].label | string | `"Age"` |  |
| listViews.default[5].items[2].key | string | `"$.metadata.creationTimestamp"` |  |
| listViews.default[5].items[2].type | string | `"duration"` |  |
| listViews.default[5].items[3].label | string | `"Ready"` |  |
| listViews.default[5].items[3].key | string | `"$.status.conditions[?(@.type==\"Ready\")].status"` |  |
| listViews.default[6].include[0] | string | `"kustomize.toolkit.fluxcd.io/kustomizations"` |  |
| listViews.default[6].exclude[0] | string | `"*"` |  |
| listViews.default[6].items[0].label | string | `"Name"` |  |
| listViews.default[6].items[0].key | string | `"$.metadata.name"` |  |
| listViews.default[6].items[0].width | int | `4` |  |
| listViews.default[6].items[1].label | string | `"Age"` |  |
| listViews.default[6].items[1].key | string | `"$.metadata.creationTimestamp"` |  |
| listViews.default[6].items[1].type | string | `"duration"` |  |
| listViews.default[6].items[2].label | string | `"Ready"` |  |
| listViews.default[6].items[2].key | string | `"$.status.conditions[?(@.type==\"Ready\")].status"` |  |
| listViews.default[7].include[0] | string | `"source.toolkit.fluxcd.io/gitrepositories"` |  |
| listViews.default[7].exclude[0] | string | `"*"` |  |
| listViews.default[7].items[0].label | string | `"Name"` |  |
| listViews.default[7].items[0].key | string | `"$.metadata.name"` |  |
| listViews.default[7].items[0].width | int | `2` |  |
| listViews.default[7].items[1].label | string | `"URL"` |  |
| listViews.default[7].items[1].key | string | `"$.spec.url"` |  |
| listViews.default[7].items[1].width | int | `4` |  |
| listViews.default[7].items[2].label | string | `"Age"` |  |
| listViews.default[7].items[2].key | string | `"$.metadata.creationTimestamp"` |  |
| listViews.default[7].items[2].type | string | `"duration"` |  |
| listViews.default[7].items[3].label | string | `"Ready"` |  |
| listViews.default[7].items[3].key | string | `"$.status.conditions[?(@.type==\"Ready\")].status"` |  |
| getViews.default[0].include[0] | string | `"*"` |  |
| getViews.default[0].exclude | list | `[]` |  |
| getViews.default[0].items[0].label | string | `"Metadata"` |  |
| getViews.default[0].items[0].key | string | `"$.metadata"` |  |
| getViews.default[0].items[1].label | string | `"Spec"` |  |
| getViews.default[0].items[1].key | string | `"$.spec"` |  |
| getViews.default[0].items[2].label | string | `"Status"` |  |
| getViews.default[0].items[2].key | string | `"$.status"` |  |
| getViews.default[1].include[0] | string | `"configmaps"` |  |
| getViews.default[1].exclude[0] | string | `"*"` |  |
| getViews.default[1].items[0].label | string | `"Metadata"` |  |
| getViews.default[1].items[0].key | string | `"$.metadata"` |  |
| getViews.default[1].items[1].label | string | `"Data"` |  |
| getViews.default[1].items[1].key | string | `"$.data"` |  |
| getViews.default[2].include[0] | string | `"secrets"` |  |
| getViews.default[2].exclude[0] | string | `"*"` |  |
| getViews.default[2].items[0].label | string | `"Metadata"` |  |
| getViews.default[2].items[0].key | string | `"$.metadata"` |  |
| getViews.default[2].items[1].label | string | `"Data"` |  |
| getViews.default[2].items[1].key | string | `"$.data"` |  |
| users[0].username | string | `"admin"` |  |
| users[0].password | string | `"8b7dc261075761e519143ccd1cf56e6d58961089bf523326a30b4cde0bcaf529"` |  |
| users[0].groups[0] | string | `"schwifty-admin-users"` |  |
| users[1].username | string | `"dev"` |  |
| users[1].password | string | `"8b7dc261075761e519143ccd1cf56e6d58961089bf523326a30b4cde0bcaf529"` |  |
| users[1].groups[0] | string | `"schwifty-dev-users"` |  |
| users[2].username | string | `"support"` |  |
| users[2].password | string | `"8b7dc261075761e519143ccd1cf56e6d58961089bf523326a30b4cde0bcaf529"` |  |
| users[2].groups[0] | string | `"schwifty-support-users"` |  |
| config.logLevel | string | `"info"` |  |
| config.originUrl | string | `"https://app.schwifty.fr"` |  |
| config.portforwardUrl | string | `"https://portforward.example.com"` |  |
| config.api.customization.enabled | bool | `true` |  |
| config.api.customization.namespace | string | `"{{ .Release.Namespace}}"` |  |
| config.api.discovery.enabled | bool | `true` |  |
| config.api.discovery.clusters[0].name | string | `"my-prod-cluster"` |  |
| config.api.discovery.clusters[0].mainUrl | string | `"https://api.example.com"` |  |
| config.api.discovery.clusters[0].portforwardUrl | string | `"{{ .Values.config.portforwardUrl }}"` |  |
| config.api.discovery.clusters[0].customizationRef | string | `"{{ (index .Values.config.api.discovery.clusters 0).name }}"` |  |
| config.api.discovery.clusters[0].authenticationRef | string | `"{{ (index .Values.config.api.discovery.clusters 0).name }}"` |  |
| config.api.discovery.clusters[0].discoveryRef | string | `"{{ (index .Values.config.api.discovery.clusters 0).name }}"` |  |
| config.api.discovery.clusters[1].name | string | `"my-staging-cluster"` |  |
| config.api.discovery.clusters[1].mainUrl | string | `"https://api.staging.example.com"` |  |
| config.api.discovery.clusters[1].portforwardUrl | string | `"https://portforward.staging.example.com"` |  |
| config.api.discovery.clusters[1].customizationRef | string | `"{{ (index .Values.config.api.discovery.clusters 0).name }}"` |  |
| config.api.discovery.clusters[1].authenticationRef | string | `"{{ (index .Values.config.api.discovery.clusters 0).name }}"` |  |
| config.api.discovery.clusters[1].discoveryRef | string | `"{{ (index .Values.config.api.discovery.clusters 0).name }}"` |  |
| config.api.authentication.noAuth.enabled | bool | `false` |  |
| config.api.authentication.noAuth.groups | list | `[]` |  |
| config.api.authentication.basic.enabled | bool | `true` |  |
| config.api.authentication.basic.salt | string | `"Aingeithoo9lainaitixes5Jaid7te"` |  |
| config.api.authentication.basic.secretRef.name | string | `"schwifty-basic-auth"` |  |
| config.api.authentication.basic.secretRef.namespace | string | `"{{ .Release.Namespace}}"` |  |
| config.api.authentication.externalOidc.enabled | bool | `false` |  |
| config.api.authentication.externalOidc.oidc.clientId | string | `"oidc-client-id"` |  |
| config.api.authentication.externalOidc.oidc.clientSecret | string | `"oidc"` |  |
| config.api.authentication.externalOidc.oidc.issuerUrl | string | `"https://oidc-issuer-url"` |  |
| config.api.authentication.externalOidc.oidc.redirectUrl | string | `"https://app.schwifty.fr/discovery"` |  |
| config.api.authentication.externalOidc.oidc.groupsClaim | string | `"cognito:groups"` |  |
| config.api.authentication.externalOidc.oidc.usernameClaim | string | `"cognito:username"` |  |
| config.api.authentication.externalOidc.oidc.groupsPrefix | string | `"schwifty-"` |  |
| config.api.authentication.kubernetesOidc.enabled | bool | `false` |  |
| config.api.authentication.kubernetesOidc.oidc.clientId | string | `"oidc-client-id"` |  |
| config.api.authentication.kubernetesOidc.oidc.clientSecret | string | `"oidc"` |  |
| config.api.authentication.kubernetesOidc.oidc.issuerUrl | string | `"https://oidc-issuer-url"` |  |
| config.api.authentication.kubernetesOidc.oidc.redirectUrl | string | `"https://app.schwifty.fr/discovery"` |  |
| config.api.authentication.kubernetesOidc.oidc.groupsClaim | string | `"cognito:groups"` |  |
| config.api.authentication.kubernetesOidc.oidc.usernameClaim | string | `"cognito:username"` |  |
| config.api.authentication.kubernetesOidc.oidc.groupsPrefix | string | `"schwifty-"` |  |
| config.port.api | int | `16666` |  |
| config.port.portforward | int | `16667` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
