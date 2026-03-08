# 1Password Connect

This deploys 1Password Connect and Operator via Helm chart.

## Prerequisites

Before deploying via ArgoCD, you must manually create the required secrets:

### 1. Create the namespace

```bash
kubectl create namespace 1password
```

### 2. Create the credentials secret

Download your `1password-credentials.json` from [1Password Connect Server](https://my.1password.com/integrations/infrastructure-secrets/connect).

```bash
kubectl create secret generic op-credentials \
  --from-file=1pass-creds=1password-credentials.json \
  -n 1password
```

### 3. Create the token secret

Generate an access token for your Connect server and create the secret:

```bash
kubectl create secret generic onepassword-token \
  --from-literal=token=YOUR_CONNECT_TOKEN \
  -n 1password
```

## Deployment

After creating the secrets, add the 1password app to your cluster's overlay:

```yaml
# argocd-apps/manifests/overlays/<cluster>/kustomization.yaml
resources:
- ../../1password/overlays/<cluster>
```

ArgoCD will deploy the Connect server and Operator automatically.

## Verification

```bash
# Check pods are running
kubectl get pods -n 1password

# Check Connect server logs
kubectl logs -l app=onepassword-connect -n 1password
```
