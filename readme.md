Install 
WSL Ubuntu 22.04
Container Container Toolkit
# Add NVIDIA Container Toolkit repository
curl -s -L https://nvidia.github.io/libnvidia-container/gpgkey | sudo apt-key add -
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/libnvidia-container/$distribution/libnvidia-container.list | sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list

# Update and install the toolkit
sudo apt-get update
sudo apt-get install -y nvidia-docker2
sudo systemctl restart docker

nvidia-smi

nvcc -- version

test
docker run -- rm -- gpus all nvidia/cuda:12.6.3-base-ubuntu20.04 nvidia-smi

Install minikube
# Download the Minikube binary
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

# Install Minikube
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Verify installation
minikube version

Start minikube
minikube start -- driver docker -- container-runtime docker -- gpus all -- cpus 16 -- memory 10000
Nvidia Plugin kubectl create -f https://raw.githubusercontent.com/NVIDIA/k8s-device-plugin/v0.15.0/deployments/static/nvidia-device-plugin.yml
ArgoCD
HashiCorp Vault https://helm.releases.hashicorp.com
External Secrets https://charts.external-secrets.io
Lilypad Argo Repo https://github.com/arsen3d/argocd-example-apps