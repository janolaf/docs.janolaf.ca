---
id: podman-pods
title: "Pods"
tags: [podman, pod]
---

The real power of podman is through the use of pods. A pod is a group of one or more containers which share the same network, pid and ipc namespace. This means that each container in a pod sees each other as being on localhost.

## creating pod

to create a pod

```bash
podman pod create --name mealie --port 8080:80
```

This creates a pod named mealie, which can be access from port 8080 on the host. To access the application, you have to publish the port from the pod, not the container.

:::note
My convention is to name the pod by the application I am trying to run.
:::

## Adding containers

To add a container to a pod, add `--pod pod-name` when creating the container.

For mealie, we will add mealie-api.

```bash
podman container create --name mealie-api --pod mealie \
	 --replace \
   -v /srv/mealie/data:/app/data:z \
   -e ALLOW_SIGNUP=true \
   -e MAX_WORKERS=1 \
   -e WEB_CONCURRENCY=1 \
   --tz=local \
   -e BASE_URL=http://mealie.foo.com \
    hkotel/mealie:api-v1.0.0beta-5
```
