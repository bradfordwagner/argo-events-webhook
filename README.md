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
helm upgrade -n argo-events -i events-webhook .
```
