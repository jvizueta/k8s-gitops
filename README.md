# argocd-apps

This is a **public Argo CD "App of Apps" repository**.
It defines which applications should be deployed in the cluster, and from where.

## Structure
- `root-app.yaml` → The **App of Apps** entrypoint for Argo CD.
- `projects/` → Argo CD **AppProjects** (security boundaries for dev and prod).
- `apps/` → Applications or ApplicationSets for each app (e.g., nginx).

## Namespace policy
Projects are configured to allow deployments **only to namespaces that end with**:
- `-dev` for development
- `-prod` for production

## Bootstrap Instructions

1. **Install Argo CD** (if not already):
   ```bash
   kubectl create ns argocd
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
