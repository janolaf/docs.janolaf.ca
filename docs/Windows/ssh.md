---
id: windows-openssh
title: OpenSSH
---
# OpenSSH in Windows
:::caution

This has only been tested with users which have administrative privilege.
May not work with a standard user.

:::

You can manage ssh keys in Windows 10/11 the same way you do in linux, with the `config` file. The `config` file is stored in `C:\Users\Foo\.ssh\config`. 

:::tip

Windows will translate `/` to `\` within OpenSSH `config` file.

The unix `~`, which refers to a user home directory, is supported by Windows in OpenSSH `config` file. You can use `~` to refer to a key in a user home directory. This will work in both Powershell and CMD.

Since unix syntax is supported, we can literally copy a `config` from a unix/linux system to a Windows system.

:::
