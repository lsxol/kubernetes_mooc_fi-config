# kubernetes_mooc_fi-config

Kubernetes configuration of the todo project from [kubernetes_mooc_fi](https://github.com/lsxol/kubernetes_mooc_fi). ArgoCD deploys the cluster from this repository; the application code lives in the code repository.

- `base` holds the manifests of the frontend, the backend and the broadcaster
- `overlays/staging` deploys to the `project-staging` namespace: the broadcaster only logs the messages and the database is not backed up
- `overlays/production` deploys to the `project-production` namespace
- `argocd` holds the ArgoCD applications, apply them once with `kubectl apply -n argocd -f argocd/`

The image tags in the overlays are updated by the GitHub Actions workflow of the code repository: a push to master releases to staging, a pushed tag releases to production.
