---
title: WSL2 Jekyll installation Help
#date: 2022-06-29 21:25:00 +0200
categories: [Guide, Notes]
tags: [ansible, jinja2, guide]
---
# Ansible Jinja2 helpers

This post is holding different good to know functions of Jinja2 templating. They are mainly for use with Ansible, but might work in any language that support jinja2 - like Python.  

Well Known (easy to find):

The Default jinja2 clause:
```yaml
{{ Ifnovariableexistremoveme | default(omit) }}
{{ Ifnovariableexistwritenull | default('null') }}
{{ Ifidontexistwriteanothervariable | default(othervar) }}
```


Lesser Known:

Generate list from nested vars:
```yaml
somenestedvar:
    var1:
    - value1
    - value2
    var2:
    - value2
    - value3

    debug:
        msg: "{{ somenestedvar.values() | flatten | unique }}
    # generates a unique list of values from somenestedvar the .values() shows the values of the variable.
```