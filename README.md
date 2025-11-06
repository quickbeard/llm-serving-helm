# Helm charts for serving LLMs

## Charts

- vLLM (NVIDIA device plugin required): inference and serving engine for LLMs.

`helm upgrade --install vllm charts/vllm --namespace vllm --create-namespace -f values/production/vllm.yaml`

- CloudNativePG (should be installed in a separate namespace, i.e. `cnpg-system`): PostgreSQL operator.

`helm upgrade --install cloudnative-pg charts/cloudnative-pg --namespace cnpg-system --create-namespace -f values/production/cloudnative-pg.yaml`

- PostgreSQL (CloudNativePG required)

`helm upgrade --install pg-cluster charts/pg-cluster --namespace pg-cluster --create-namespace -f values/production/pg-cluster.yaml`

- LiteLLM (PostgreSQL required): LLM Gateway to call 100+ LLMs, load balance, cost tracking across projects.

`helm upgrade --install litellm charts/litellm --namespace litellm --create-namespace -f values/production/litellm.yaml`

## Dependencies

- NVIDIA device plugin: used to manage NVIDIA GPUs in a K8s cluster.

`helm upgrade --install nvidia-device-plugin charts/nvidia-device-plugin --namespace nvidia-device-plugin --create-namespace -f values/production/nvidia-device-plugin.yaml`

- CSI driver for NFS (should be installed in `kube-system` namespace): supports dynamic provisioning of Persistent Volumes via Persistent Volume Claims by creating a new sub directory under NFS server.

`helm upgrade --install csi-driver-nfs charts/csi-driver-nfs --namespace kube-system -f values/production/csi-driver-nfs.yaml`
