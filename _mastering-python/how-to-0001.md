---
title: "Using Powershell"
permalink: /mastering-python/how-to-0001/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 255, 0, 0.5)
  teaser: "/assets/images/misc/how-to-1.jpg"
classes: wide
excerpt: "How-To #1: List running Services"
---

# List running services

#### Windows:
The below command lists all the sevices that are currently running on a Windows PC using Powershell:

```powershell
Get-Service | Where-Object {$_.Status –eq “Running”}
```

#### MacOS:
On a MacOS, the following command can be used on a terminal:

```terminal
ps aux
```

The above command lists all the services. To list only specific services, we can use the below command

```terminal
ps aux | grep <process-name>
```

`<process-name>` needs to be replaced with the process that you are looking for.
