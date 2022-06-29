---
title: WSL2 Jekyll installation Help
date: 29/06.2022 21:00
categories: [Guide, Help, Development]
tags: [dev, wsl, guide]
---
# Config help
```
sudo apt-get update -y && sudo apt-get upgrade -y

sudo apt install ruby-full

sudo apt-get install make gcc gpp build-essential zlib1g zlib1g-dev ruby-dev dh-autoreconf

sudo gem update

sudo gem install bundler

# if you get errors (as I've done), go back to the start and go through these commands again
#sudo gem install jekyll

# inside jekyll repo
bundle install

# simple serve
bundle exec jekyll serve

```