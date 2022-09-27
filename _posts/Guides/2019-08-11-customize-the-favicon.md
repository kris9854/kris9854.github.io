---
title: Customize the Favicon
author: cotes
date: 2022-09-27 17:45:00 +0200
categories: [Blogging, Tutorial]
tags: [favicon]
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
The Ansible01 machines has been setup so that I can connect through VS: Code towards that. I have setup ssh and gpg keys so that I can sign my commits towards Github.

My ~/.gitcommit file has the following setup:

```bash
[user]
    email = redacted
    name = redacted
    signingkey = redacted

[commit]
        gpgsign = true

[trailer "sign"]
    key = "Signed-off-by:"
    ifmissing = add
    ifexist =doNothing
    command = echo "$(git config user.name) <$(git config user.email>"

```