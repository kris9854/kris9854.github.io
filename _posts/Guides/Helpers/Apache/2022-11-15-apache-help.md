---
title: Apache/HTTPD Helper
author: Kristian
date: 2022-11-15 21:10:00 +0200
categories: [Guide, Information]
tags: [apache, webpage]
---

Reminder of RewriteRule flags :

| RewriteRule Flags | What it does |
|-------------------|--------------|
| L | Last. Stop processing RewriteRules once this one matches. Order counts! |
| C | Chain. Continue processing the next RewriteRule. If this rule doesn't match, then the next rule won't be executed. More on this  |later.
| E | Set environmental variable. Apache has various environmental variables that can affect web-server behavior. |
| F | Forbidden. Returns a 403-Forbidden error if this rule matches. |
| G | Gone. Returns a 410-Gone error if this rule matches. |
| H | Handler. Forces the request to be handled as if it were the specified MIME-type. |
| N | Next. Forces the rule to start over again and re-match. BE CAREFUL! Loops can result. |
| NC | No case. Allows [jpg] to match both jpg and JPG. |
| NE | No escape. Prevents the rewriting of special characters (. ? # & etc) into their hex-code equivalents. |
| NS | No subrequests. If you're using server-side-includes, this will prevent matches to the included files. |
| P | Proxy. Forces the rule to be handled by mod_proxy. Transparently provide content from other servers, because your web-server  |fetches it and re-serves it. This is a dangerous flag, as a poorly written one will turn your web-server into an open-proxy and That is Bad.
| PT | Pass Through. Take into account Alias statements in RewriteRule matching. |
| QSA | QSAppend. When the original string contains a query (http://example.com/thing?asp|foo) append the original query string to the  |rewritten string. Normally it would be discarded. Important for dynamic content.
| R | Redirect. Provide an HTTP redirect to the specified URL. Can also provide exact redirect code [R|303]. Very similar to  |RedirectMatch, which is faster and should be used when possible.
| S | Skip. Skip this rule. |
| T | Type. Specify the mime-type of the returned content. Very similar to the AddType directive. |

Example
```shell
RewriteCond %{HTTP_HOST} ^[^.]+\.[^.]+$ [NC]
RewriteRule ^ https://www.%{HTTP_HOST}%{REQUEST_URI} [R=301,L,NE]
```

Example 1 - Redirect example.com to www.example.com:
```shell
RewriteEngine On
RewriteCond %{HTTP_HOST} !^www.example.com$ [NC]
RewriteRule ^(.*)$ http://www.example.com/$1 [L,R=301]
```
Example 2 - Redirect www.example.com to example.com:
```shell
RewriteEngine on
RewriteCond %{HTTP_HOST} ^www\.example\.com$
RewriteRule ^/?$ "http\:\/\/example\.com\/" [R=301,L]
```


Links:
- [Help on rewrite](https://cheatography.com/davechild/cheat-sheets/mod-rewrite/)