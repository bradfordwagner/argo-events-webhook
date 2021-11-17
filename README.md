# private-events-webhook

```bash
kaf github.secret.yaml
kaf github.eventsource.yaml

kn argo-events
svc=bradfordwagner-eventsource-svc
host=$(kubectl get svc ${svc} -o json | jq '.status.loadBalancer.ingress[0].ip' -r)
port=$(kubectl get svc ${svc} -o json | jq '.spec.ports[0].port' -r)
echo "${host}:${port}" | pbcopy

```

## Helpers
```bash
# sensors
watchexec -cr "kubectl delete -n argo-events -f github.branches.sensor.yaml; kubectl apply -n argo-events -f github.branches.sensor.yaml"
watchexec -cr "kubectl delete -n argo-events -f github.tags.sensor.yaml; kubectl apply -n argo-events -f github.tags.sensor.yaml"

```