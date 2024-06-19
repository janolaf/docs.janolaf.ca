---
id: windows-openssh
title: OpenSSH
---

# OpenSSH in Windows

:::caution

This has only been tested with users which have administrative privilege.
May not work with a standard user.

:::

## Create SSH key

```
ssh-keygen.exe -t ed25519
```

The default location ssh keys are stored is `C:\User\username\.ssh\`. The directory will be created when you generate your first ssh key.

## Managing mutliple SSH keys

You do not need a third party application, like putty, to manage multiple SSH keys. We can manage SSH keys in Windows 10/11 the same way we do on unix or linux system; using OpenSSH `config` file. The `config` file is stored in `C:\Users\username\.ssh\config`.

:::tip

Windows will translate `/` to `\` within OpenSSH `config` file.

The unix `~`, which refers to a user home directory, is supported by Windows in OpenSSH `config` file. You can use `~` to refer to a key in a user home directory. This will work in both Powershell and CMD.

Since unix syntax is supported, we can copy a `config` from a unix/linux system to a Windows system.

:::
