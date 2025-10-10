# Helm charts for serving LLMs

CSI driver for NFS: `helm upgrade --install csi-driver-nfs . --namespace kube-system`

NVIDIA device plugin: `helm upgrade --install nvidia-device-plugin . --namespace nvidia-device-plugin --create-namespace`

vLLM: `helm upgrade --install vllm . --namespace vllm --create-namespace -f values.yaml`
