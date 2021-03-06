Before we run a Pipeline we have to recognize that pipelines will run tasks that will eventually need access to restricted resources such as repositories (e.g., Git) and registries (e.g., container and chart registries). These resources are accessed through secrets. To use secrets, the Pipelines are associated with service accounts. The service accounts have roles that allow them to access specific Kubernetes Secrets.

Before we can proceed, set up a ServiceAccount.

`kubectl create -f pipeline/service-account.yaml`{{execute}}

This example is simple because both the readability of the source code repo and the container image registry are not protected with a secret. Therefore, we are just setting up a simple role.

Now a ServiceAccount named "service-account" is defined.

`kubectl get ServiceAccounts`{{execute}}

In the next step, this ServiceAccount will be referenced by the PipelineRun.
