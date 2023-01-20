# Helm Chart for SSL Certificate Exporter

![Version: 2.4.1](https://img.shields.io/badge/Version-2.4.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.1.0](https://img.shields.io/badge/AppVersion-0.1.0-informational?style=flat-square)

# Usage
1. Add helm repo
```
helm repo add ssl-exporter https://xjulio.github.io/ssl_exporter
```

2. Update repo charts
```
helm repo update ssl-exporter
```

3. Install chart
```
helm -n monitoring install ssl-exporter ssl-exporter/ssl-exporter --version 2.4.1 --create-namespace
```

4. Check chart deployment
```
helm -n monitoring list
NAME        	NAMESPACE 	REVISION	UPDATED                             	STATUS  	CHART             	APP VERSION
ssl-exporter	monitoring	1       	2022-06-03 05:07:14.791488 +0100 IST	deployed	ssl-exporter-2.4.1	0.1.0
```

5. Check k8s resources
```
kubectl -n monitoring get po
NAME                            READY   STATUS    RESTARTS   AGE
ssl-exporter-76b484c8bb-czmbd   1/1     Running   0          73s
ssl-exporter-76b484c8bb-wv9km   1/1     Running   0          73s
```


## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Affinity for controller pod assignment |
| annotations | object | `{}` | Add annotations to all the deployed resources |
| configMap.data | string | | ssl-exporter modules configuration |
| configMap.enabled | bool | `true` | Enable ssl-exporter modules configuration to be mounted as volume config map. |
| fullnameOverride | string | `""` | String to fully override chart fullname template |
| image.pullPolicy | string | `"IfNotPresent"` | sll-exporter image pull policy |
| image.repository | string | `"docker.io/xjulio/ssl-exporter"` | ssl-exporter qualified image repository |
| image.sha | string | `""` | ssl-exporter image sha |
| image.tag | string | `"latest"` | ssl-export image tag |
| imagePullSecrets | list | `[]` | Specify docker-registry secret names as an array |
| nameOverride | string | `""` | String to partially override chart name include (will maintain the release name) |
| namespaceOverride | string | `""` | String to override chart namespace |
| nodeSelector | object | `{}` | Node labels for controller pod assignment |
| probes.enableLivenessProbe | bool | `true` | Enable livenessProbe |
| probes.enableReadinessProbe | bool | `true` | Enable readinessProbe |
| probes.livenessProbe.failureThreshold | int | `3` | Failure threshold for livenessProbe |
| probes.livenessProbe.initialDelaySeconds | int | `3` | Initial delay seconds for livenessProbe |
| probes.livenessProbe.periodSeconds | int | `5` | Period seconds for livenessProbe |
| probes.livenessProbe.successThreshold | int | `1` | Success threshold for livenessProbe |
| probes.livenessProbe.timeoutSeconds | int | `5` | Timeout seconds for livenessProbe |
| probes.readinessProbe.failureThreshold | int | `3` | Failure threshold for readinessProbe |
| probes.readinessProbe.initialDelaySeconds | int | `3` | Initial delay seconds for readinessProbe |
| probes.readinessProbe.periodSeconds | int | `5` | Period seconds for readinessProbe |
| probes.readinessProbe.successThreshold | int | `1` | Success threshold for readinessProbe |
| probes.readinessProbe.timeoutSeconds | int | `5` | Timeout seconds for readinessProbe |
| prometheusOperator.enableExampleProbes | bool | `false` | Enable deployment of sample prometheus probes |
| rbac.create | bool | `true` | Specifies whether to install and use RBAC rules |
| replicaCount | int | `2` | Number of ssl-exporter pods to load balance between |
| resources.create | bool | `true` | Enable resources restrictions to the ssl-exporter container |
| resources.limits | object | `{"cpu":"500m","memory":"256Mi"}` | The resources limits for the container |
| resources.requests | object | `{"cpu":"200m","memory":"128Mi"}` | The requested resources for the container |
| securityContext.definition.allowPrivilegeEscalation | bool | `false` | Enables privilege Escalation context for the pod. |
| securityContext.definition.capabilities.drop | list | `["ALL"]` | Drop capabilities for the securityContext |
| securityContext.definition.readOnlyRootFilesystem | bool | `true` | Allows the pod to mount the RootFS as ReadOnly |
| securityContext.definition.runAsNonRoot | bool | `true` | Set pod Security Context runAsNonRoot |
| securityContext.enabled | bool | `true` | Enabled ssl-expoeter container Security Context |
| service.annotations | object | `{}` | Annotations for the ssl-exporter service |
| service.labels | object | `{}` | Extra labels for the ssl-exporter service |
| service.port | int | `9219` | ssl-exporter service port |
| service.type | string | `"LoadBalancer"` | How the Service is exposed. Defaults to ClusterIP. Valid options are ClusterIP, NodePort, LoadBalancer, ExternalName ref: https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types |
| serviceAccount | object | `{"annotations":{},"create":true,"name":null}` | Service account for ssl-exporter to use. ref: https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/ |
| serviceAccount.annotations | object | `{}` | Annotations for service account. Evaluated as a template. Only used if create is true. |
| serviceAccount.create | bool | `true` | Specifies whether a ServiceAccount should be created |
| serviceAccount.name | string | `nil` | Name of the service account to use. If not set and create is true, a name is generated using the fullname template. |
| terminationGracePeriodSeconds | int | `0` | In seconds, time the given to the ssl-exporter pod needs to terminate gracefully |
| tlsConfigSecret.enabled | bool | `false` | Enable a custom secret to be mounted |
| tlsConfigSecret.mountPath | string | `"/etc/tls"` | Path where the secret will be mounted inside the container |
| tlsConfigSecret.secretName | string | `""` | Secret name to be mounted. Secret must exists in the same namespace where the chart is deployed. |
| tolerations | list | `[]` | Tolerations for controller pod assignment |
