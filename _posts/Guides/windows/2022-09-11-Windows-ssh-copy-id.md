---
title: Windows ssh-copy-id
author: Kristian
date: 2022-09-11 17:34:00 +0200
categories: [Blogging, Tutorial]
tags: [Windows, ssh]
---
# Windows OpenSSH equivalent of ssh-copy-id

ssh-copy-id is a awesome command to copy a ssh-key to a remote server.  
It copies the public key of your ssh key to the remote server, making you able to login without using a password.

On linux normally you would use the ssh-copy-id command, but this command doesn't work for Windows. Therefore you should use the following command for windows.
> ONLY copies the public key to the remote host
```powershell
# Copy id_rsa.pub to the remote aiuthorized server
get-content $env:USERPROFILE\.ssh\id_rsa.pub | ssh USER@IP-ADDRESS "cat >> .ssh/authorized_keys"
```

And to copy from linux to linux machine use this command:
> It only copies the public key to the remote host
```bash
ssh-copy-id -i ~/.ssh/id_rsa USER@IP-ADDRESS
```