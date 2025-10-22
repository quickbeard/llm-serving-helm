# Helm charts for serving LLMs

CSI driver for NFS: `helm upgrade --install csi-driver-nfs . --namespace kube-system -f ../../values/production/csi-driver-nfs.yaml`

NVIDIA device plugin: `helm upgrade --install nvidia-device-plugin . --namespace nvidia-device-plugin --create-namespace -f ../../values/production/nvidia-device-plugin.yaml`

vLLM: `helm upgrade --install vllm . --namespace vllm --create-namespace -f ../../values/production/vllm.yaml`
