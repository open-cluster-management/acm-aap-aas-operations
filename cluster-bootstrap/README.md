# ACM AAP monitoring hub cluster bootstrap

This folder contains the artifacts with conrfiguration and related Argocd applications that helps to deploy ACM hub management layer on top of the AAPaaS offering.

## Deploying Hub Services on a New Cluster

### Prerequisites:
Make sure all secrets(path and key) are put in Vault defore the deployment. Please refer to the secret defination doc here:
https://docs.google.com/document/d/1E5n62ed9-ls3rIIPqd8SoTM2W9OzC6xQTq6jQc11fsA/edit


### Deployment:
1. Replace the `VAULT_ADDRESS` and `VAULT_TOKEN` in `cluster-bootstrap/openshift-gitops/config/argocd.yaml` with the Vault service address and auth token which are available in above doc.
2. Run `make deploy-dev-all`.


### Configrations layout:
    cluster-bootstrap
    ├── alert-manager-config
    │   └── base
    │       └── alertmgr-policy-conf.yaml    # Alert manager policy configration
    ├── grafana-dev
    │   └── base                             # Grafana dev instance configration
    ├── multicluster-observability
    │   └── base
    │       ├── custom-alerts                # Custom alerts configration
    │       ├── custom-metrics               # Custom metrics configration
    │       ├── dashboard                    # Custom Grafana dashboard configration
    │       └── deploy                       # Multicluster observability configration
    └── prometheus-config                    
        └── base                             # Prometheus configration
