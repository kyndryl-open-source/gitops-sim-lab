# SRE@Kyndryl

## SRE Public Labs - GITOPS Sim

* Version: `0.1.0`
* License: `MIT`

### Architecture

###

###


kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
### Learning objectives

* Learn how to deploy an app using GitOps approach

* Learn how use Argo CD

### Pre-requisite knowledge

*	Familiarity with Kubernetes

*	Basic notions on Node.js (JavaScript) programming language

*	Good understanding of YAML (Yet Another Markup Language)

### Kubernetes cluster

This lab runs on any K8s cluster with few adjusts on the ingresses, we recommend using a free trial account on Google Cloud Platform. You can create one through this [documentation](https://cloud.google.com/free). You can download and install the Google CLI `gcloud` by checking this [document](https://cloud.google.com/sdk/docs/install).

In case you use a GCP account for this lab, we provided the Google Kubernetes Engine (GKE) recommended configuration below:

* GKE Configuration

| **Parameter** | **Value** |
|:--------------------------------|:--------------------------------|
| GKE mode | `Standard with static K8s version` |
| Location type | `Zonal` |
| Release channel | `None` |
| Kubernetes version | `v1.24.6-gke.1500` |
| Number of nodes | `3` |
| Machine type | `e2-medium` |
| Image type | `cos_containerd` |
| | |

* GKE cluster creation

You can create a K8s cluster for this lab with the following commands:

```
gcloud auth login
gcloud container clusters create cluster-1 --no-enable-autoupgrade --enable-service-externalips --enable-kubernetes-alpha --region=<your_closest_region> --cluster-version= v1.24.6-gke.1500 --machine-type=e2-medium --monitoring=NONE
```

* kubectl configuration

You can configure your local `kubectl` environment and credentials with the following command:

```
gcloud container clusters get-credentials cluster-1 --zone <your_closest_region> --project <your_project_id>
```

### Contents

*

### Installation

* Argo CD

```
cd argo-cd
./install.sh
```

* More information [here](https://argo-cd.readthedocs.io/en/stable/getting_started/)


### Configuration

* Environmental Variables

process.env
```
#!/bin/bash

export ARGOCD_ADMIN_NAME="admin"
export APP_NAME="simple-node-api"
export APP_REPO_URL="https://github.com/kyndryl-open-source/gitops-app-examples.git"
export APP_REPO_PATH="simple-node-api"
```

### Deployment

* Simple Node API

```
cd argo-cd
./deploy.sh
```

## End of document
