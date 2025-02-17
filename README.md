# Synchronization at workflow level

Tested in argo: 
  v3.6.2

```bash
export SERVICE_ACCOUNT=argo-workflow
export NAMESPACE=argo
curl -O https://raw.githubusercontent.com/G0erman/hello-argo-workflows/refs/heads/master/hello_argo_workflows/syncronization/my-config.yaml
curl -O https://raw.githubusercontent.com/G0erman/hello-argo-workflows/refs/heads/master/hello_argo_workflows/syncronization/synchronization-wf-level.yaml
kubectl apply -n $NAMESPACE -f my-config.yaml
argo submit --serviceaccount $SERVICE_ACCOUNT --watch synchronization-wf-level.yaml
```

```bash
$ kubectl get configmaps -n argo
NAME                            DATA   AGE
kube-root-ca.crt                1      5m15s
minio-config                    1      5m8s
my-config                       2      62s
workflow-controller-configmap   2      5m11s
```

! Ref:

* https://argo-workflows.readthedocs.io/en/latest/synchronization
