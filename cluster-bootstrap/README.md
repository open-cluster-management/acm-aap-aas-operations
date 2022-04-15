# ACM AAP monitoring hub cluster bootstrap

This folder contains the artifacts with configuration and related Argocd applications that helps to deploy ACM hub management layer on top of the AAPaaS offering.

## Deploying Hub Services on a New Cluster


### Prerequisites:
Please check the following doc which contains the tokens need to use during the cluster bootstrap deployment.
https://docs.google.com/document/d/1E5n62ed9-ls3rIIPqd8SoTM2W9OzC6xQTq6jQc11fsA/edit


### Deployment:
1. Replace the `VAULT_ADDRESS` and `VAULT_TOKEN` in `cluster-bootstrap/openshift-gitops/config/argocd.yaml` with the Vault service address and auth token from above doc.
   Please note that to used the correct env values for your deployment. 
   * Dev is for development env usage. 
   * Stage is for staging env usage.
2. Deploy the stacks:
   * For bootstrap development env, run `make deploy-dev`.
   * For bootstrap development env based on private cluster, run `deploy-dev-private`.
   * For bootstrap stage env, run `make deploy-stage`.


### Configurations layout:
    cluster-bootstrap
    ├── acm                                 # Deploy ACM
    │   ├── base
    │   └── overlay
    │       ├── dev                            
    │       └── stage        
    ├── cert-manager                        # Deploy Cert manager
    │   ├── base      
    │   └── overlay
    │       ├── dev                            
    │       └── stage                
    ├── alert-manager-config                # Deploy Alert manager policy configuration
    │   ├── base
    │   └── overlay
    │       ├── dev                            
    │       ├── dev-private                 # Add http proxy for slack alerts forwards
    │       └── stage
    ├── grafana-dev                         # Deploy Grafana dev instance configuration
    │   ├── base   
    │   └── overlay
    │       ├── dev  
    │       ├── dev-managed-premium 
    │       └── stage                             
    ├── multicluster-observability
    │   ├── base
    │   │   ├── custom-alerts                # Custom alerts configuration
    │   │   ├── custom-metrics               # Custom metrics configuration
    │   │   ├── dashboard                    # Custom Grafana dashboard configuration
    │   │   └── deploy                       # Deploy Multicluster observability
    │   └── overlay  
    │       ├── dev
    │       └── stage  
    └── prometheus-config                    # Deploy Prometheus configuration
        ├── base                             
        └── overlay  
            ├── dev
            └── stage
