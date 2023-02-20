---
id: systemd
title: "systemd"
tags: [podman, systemd, pod]
---

# Generating systemd service files

If it does not already exist, create the systemd user directory in your home directory.

```bash
mkdir -p ~/.config/systemd/user
```

Then generate the systemd service file.

For this example we will generate a service file a container called jupyter-notebook.

```bash
podman generate systemd \
	--user \
	--new \
	--name jupyter-notebook \
	-f /home/user/.config/systemd/user/
```

This will create container-jupyter.service in `~/.config/systemd/user/`. If you do not use `--name` you will get a service file named something like `container-dg6464323fsdf34536`.

After creating the service file, reload systemd.

```bash
Systemctl --user daemon-reload
```

Stop the jupyter container.

```bash
podman stop jupyter-notebook
```

Enable and start container-jupyter.service.

```bash
Systemctl --user enable --now container-jupyter-notebook.service
```

Check if everything worked

```bash
Systemctl --user status container-jupyter-notebook
```

```bash
podman container ps jupyter-notebook
```

If you want the container to be accessible when the user is not logged in, you will need to run

```bash
loginctl enable-linger user
```

This will allow services owned by the user to run without the user being logged in.
