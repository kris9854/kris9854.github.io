---
title: Cisco Anyconnect
author: Kristian
date: 2022-08-01 19:28:00 +0200
categories: [Guide, Information]
tags: [it, software]
---
# Cisco VPN AnyConnect
## Profile Setup
Generate a file called *profile.xml* within the respective path:

| Operating System | Location |
| ------------------ | --------- |
| Windows 8 | %ProgramData%\\Cisco\\Cisco AnyConnect Secure Mobility Client\\Profile |
| Windows 10 | %ProgramData%\\Cisco\\Cisco AnyConnect Secure Mobility Client\\Profile |
| Mac OS X | /opt/cisco/anyconnect/profile |
| Linux | /opt/cisco/anyconnect/profile |

The profile.xml should look like this:
```xml
<?xml version="1.0" encoding="UTF-8"?>

<AnyConnectProfile xmlns="http://schemas.xmlsoap.org/encoding/">

    <ServerList>

        <HostEntry>

            <User>AUSER</User>

            <HostName>VPN NAME</HostName>

            <HostAddress>AHOSTADDED</HostAddress>

        </HostEntry>

        <HostEntry>

            <User>AUSER</User>

            <HostName>VPN NAME</HostName>

            <HostAddress>AHOSTADDED</HostAddress>

        </HostEntry>

        <HostEntry>

            <User>AUSER</User>

            <HostName>VPN NAME</HostName>

            <HostAddress>AHOSTADDED</HostAddress>

        </HostEntry>

    </ServerList>

</AnyConnectProfile>
```
