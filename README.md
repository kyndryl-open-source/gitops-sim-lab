# SRE@Kyndryl

## SRE Public Labs - GITOPS Sim

* Version: `0.1.0`
* License: `MIT`

### Architecture


kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
