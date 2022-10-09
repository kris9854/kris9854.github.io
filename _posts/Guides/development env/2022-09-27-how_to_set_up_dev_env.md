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
| Code: alma09.lab.local | Alma Linux 9 | Ansible control node / git / git signing profiles |
| Code: win2019.lab.local | windows Server 2019 | PowerShell / git / git signing profiles |
| almatest01.lab.local | Alma Linux 9 | Ansible Test node |
| windc01.lab.local | Windows Server 2019 | Ansible Test node and LAB DC |

<br/>

## Setup
- Install linux vm on hyper-v (or other)
        - At installation choose container tools and set hostname to alma09.lab.local (example)

        ```bash
        eval NEW_USER_NAME=dev-ansible
        sudo yum upgrade -y && sudo yum update -y
        echo /etc/sudoers.d/$NEW_USER_NAME >> $NEW_USER_NAME ALL=(ALL) NOPASSWD:ALL
        sudo useradd $NEW_USER_NAME
        passwd $NEW_USER_NAME
        ```

        - Then Setup the env for the new user

        ```bash
        eval NEW_USER_NAME=dev-ansible
        mkdir --parents ~/github ~/github/ansible_repos  ~/github/ansible_roles  ~/github/repo ~/.ssh
        touch ~/.ssh/authorized_keys
        ```



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
- In your `.bash_profile`

```bash
eval NEW_USER=dev-ansible

#CONFIGS FILES
cat <<EOT >> ~/.gnupg/gpg.conf
default-key [GPG-KEY-ID]
use-agent
EOT

cat <<EOT >> ~/.gnupg/gpg-agent.conf 
use-standard-socket
default-cache-ttl 600
write-env-file /Users/$NEW_USER/.gnupg/gpg-agent-info
pinentry-program /usr/bin/pinentry
EOT

cat <<EOT >> ~/.bash_profile
# SSH AGENT
eval $(ssh-agent)
# ANSIBLE SETTINGS:
eval DEFAULT_ROLES_PATH=~/.ansible/roles:/usr/share/ansible/roles:/etc/ansible/roles:~/github ansible_roles:./roles:~/github/roles
export GPG_TTY=$(tty)
[ -f ~/.gnupg/gpg-agent-info ] && source ~/.gnupg/gpg-agent-info

if [ -S "${GPG_AGENT_INFO%%:*}" ]; then
        export GPG_AGENT_INFO
else
      eval $( gpg-agent --daemon --options ~/.gnupg/gpg-agent.conf --write-env-file ~/.gnupg/gpg-agent-info )
fi
EOT
#REFRESH
killall gpg-agent
. ~/.bash_profile

```