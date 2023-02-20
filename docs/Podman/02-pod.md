---
id: podman-pods
title: "Pods"
tags: [podman, pod]
---

The real power of podman is through the use of pods. A pod is a group of one or more containers which share the same network, pid and ipc namespace. This means that each container in a pod sees each other as being on localhost.

We can access all containers from a single port.
