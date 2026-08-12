# homeArgoCDApplication

This is the repo for my ArgoCD home installation. It makes sure all the apps are up and running. It is both a playground and a deployment environment for my applications.

## External access model

The cluster exposes a single reverse-proxy entrypoint on the host:

```text
http://<server-ip>:4445
```

Routes behind this entrypoint decide which internal Kubernetes service receives the request.

Current routes:

```text
/speedtest/ -> homeserver-service.homeserver.svc.cluster.local:1234
```

Example:

```text
http://192.168.10.128:4445/speedtest/
```

The speedtest service stays internal to the cluster. External clients should use the reverse proxy instead of connecting to a dedicated speedtest port.
