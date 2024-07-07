---
title: "Prerequisites for KRS"
weight: 20
---

Before you begin installing and using the Kubetools Recommender System (KRS), ensure that you have the following prerequisites in place:

1. **Kubernetes Cluster**: You need a Kubernetes cluster up and running. This can be:
   - A local cluster (e.g., using Docker Desktop or Minikube)
   - A cloud-based cluster (e.g., GKE, EKS, AKS)

2. **Python**: KRS requires Python 3.6 or later. You can check your Python version by running:
```python
python --version
```

3. **Kubectl**: Ensure you have kubectl installed and configured to interact with your Kubernetes cluster.

4. **Kube Config**: Make sure you have the correct kube config file set up. By default, KRS looks for the config at `~/.kube/config`. 

**Note**: If your kube config is in a different location, you'll need to provide the path when initializing KRS using the `krs init` command.

5. **pip**: The Python package installer, pip, should be installed to manage KRS dependencies.

Once you have these prerequisites in place, you're ready to move on to the [installation](../installation) process.