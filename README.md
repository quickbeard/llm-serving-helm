# Helm charts for serving LLMs

- CSI driver for NFS (should be installed in `kube-system` namespace): supports dynamic provisioning of Persistent Volumes via Persistent Volume Claims by creating a new sub directory under NFS server.

`helm upgrade --install csi-driver-nfs charts/csi-driver-nfs --namespace kube-system -f values/production/csi-driver-nfs.yaml`

- NVIDIA device plugin: used to manage NVIDIA GPUs in a K8s cluster.

`helm upgrade --install nvidia-device-plugin charts/nvidia-device-plugin --namespace nvidia-device-plugin --create-namespace -f values/production/nvidia-device-plugin.yaml`

- vLLM: inference and serving engine for LLMs (NVIDIA device plugin required).

`helm upgrade --install vllm charts/vllm --namespace vllm --create-namespace -f values/production/vllm.yaml`

- StackGres: PostgreSQL operator for K8s.

`helm upgrade --install stackgres-operator charts/stackgres-operator --namespace stackgres --create-namespace -f values/production/stackgres-operator.yaml`
