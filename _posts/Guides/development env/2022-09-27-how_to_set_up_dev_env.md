---
title: Development machine setup
author: Kristian
date: 2022-09-27 19:00:00 +0200
categories: [Guide, Environment]
tags: [Git, help]
---
# Development Setup
In this guide I will provice information on how I setup my development environment. I was using WSL 2 for long, but as my demand for communicating between multiple Virtual machines. 
My lab consists of the following machines:
| Machine name | OS | Purpose |
|--------------|----|---------|
| ansible01.lab.local | Alma Linux 9 | Ansible control node / git / git signing profiles |
| wintest.lab.local | windows 2019 | Ansible Test node |
| almatest01.lab.local | Alma Linux 9 | Ansible Test node |
| ubutest01.lab.local | ubuntu | Ansible Test node |
<br/>

To generate a GPG key you can do the following:
```shell
sudo yum install pinentry
gpg --full-generate-key
# NEEDS TO BE GITHUB USER AND MAIL + minimum 4096 bits
gpg --list-secret-keys --keyid-format=long
# the keyid is the first after sec  rsa4096/KEYIDHERE 20xx
gpg --armor --export keyid
# upload to github
# to sign commits git commit -s -S -m "Code update message"
```

The Ansible01 machines has been setup so that I can connect through VS: Code towards that. I have setup ssh and gpg keys so that I can sign my commits towards Github.
My ~/.gitconfig file has the following setup:

```shell
[user]
        email = redacted
        name = redacted
        signingkey = redacted
[commit]
        gpgsign = true

[alias]
        c = commit -s -S

[trailer "sign"]
        key = "Signed-off-by:"
        ifmissing = add
        ifexist =doNothing
        command= echo "$(git config user.name) <$(git config user.email>"
```