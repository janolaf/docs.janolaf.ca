---
id: systemd
title: "Generating service files for pods and containers"
tags: [podman, systemd, pod ]
---

# Generating systemd service file for containers

If everything is working as intended, all that is left is to generate the systemd service file, enable it and see if it works.

If it does not already exist, create the systemd user directory in your home directory.

```bash
mkdir -p ~/.config/systemd/user
```

Then generate the systemd service file.

```bash
podman generate systemd \
	--user \
	--new \
	--name foo \
	-f /home/user/.config/systemd/user/
```

This will create container-jupyter.service in `~/.config/systemd/user/`. If you do not use `--name` you will get a service file named something like `container-dg6464323fsdf34536`.

After creating the service file, reload systemd.

```bash
Systemctl --user daemon-reload
```

Stop the jupyter container.

```bash
podman stop foo
```

Enable and start container-jupyter.service.

```bash
Systemctl --user enable --now container-foo.service
```

Check if everything worked

```bash
Systemctl --user status container-foo
```

```bash
podman container ps foo
```

If you want the container to be accessible when the user is not logged in, you will need to run

```bash
loginctl enable-linger user
```

This will allow services owned by the user to run without the user being logged in.