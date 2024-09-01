# k8s-exercises

## k8s exercises

```
$ cd k8s

$ kubectl apply -f pod.yaml

$ kubectl get po

NAME   READY   STATUS    RESTARTS      AGE
echo   2/2     Running   2 (12m ago)   30m

$ kubectl exec -it echo -c nginx -- sh

$ kubectl apply -f service.yaml

$ kubectl get svc echo

NAME   TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)   AGE
echo   ClusterIP   10.43.59.220   <none>        80/TCP    2m1s

$ kubectl logs -f echo -c echo

// 別ターミナルで
$ kubectl run -i --rm --tty debug --i
mage=ghcr.io/gihyodocker/debug:v0.1.0 --restart=Never -- bash

# curl http://echo

$ kubectl delete -f pod.yaml
$ kubectl delete -f service.yaml
```

## kustomize exercises

```
$ cd ../kustomize/base

$ kustomize create --autodetect

$ kustomize build .

$ kustomize build . | kubectl apply -f

$ kustomize build . | kubectl delete -f

---

$ cd ../overlays/dev/

$ kustomize create --resources ../../base

$ kustomize edit add patch --path patch-deployment.yaml

$ kustomize build .
```
