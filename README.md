# Kubernetes manifests or Helm charts used by Argo CD applications

This repository contains the Kubernetes manifests and Helm charts used to deploy workloads via Argo CD applications.  
It serves as the source of truth for the configuration and deployment of various services and applications managed by
Argo CD.

To ensure separation of concerns three repositories are used to manage the Argo CD setup:

* Argo CD installation and
  configuration: [https://github.com/jterpstra1/argocd-setup](https://github.com/jterpstra1/argocd-setup)
* Argo CD application definitions: [https://github.com/jterpstra1/argocd-apps](https://github.com/jterpstra1/argocd-apps)
* Kubernetes manifests or Helm charts used by Argo CD
  applications: [https://github.com/jterpstra1/argocd-k8s-resources](https://github.com/jterpstra1/argocd-k8s-resources)