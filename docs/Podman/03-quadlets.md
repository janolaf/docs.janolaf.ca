---
id: podman-quadlet
title: "Quadlet"
tags: [podman, quadlet, systemd]
---

:::warning
Draft
:::

# Using Quadlets to Manage Containers

Since Podman 4.8, you can manage containers with systemd using Quadlets.
This replaces the old method `podman generate systemd`.

As of Podman 5.0, you can manage kube files, containers and pods.

A Quadlet creates and manages containers using systemd systax. With a .container file

# Deploying a Container with Quadlet

Quadlet files are stored in `/etc/containers/systemd/`, `/usr/share/containers/systemd/` or in `~/.config/containers/systemd/`

For the current example, we will use `~/.config/containers/systemd/`.

Create contaiers/systemd directory

```bash
mkdir -p ~/.config/containers/systemd/
```

Create a file in ~/.config/containers/systemd/ called `ngnix.container`

```bash
touch ~/.config/containers/systemd/ngnix.container
```

:::note

Place holder

:::

Like systemd service files, quadlet file will not register changes in the systemd directory until `systemctl daemon-reload` is run.

```bash
systemctl --user deamon-reload
```
