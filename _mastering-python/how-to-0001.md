---
title: "How-To"
excerpt: "A tabby is any domestic cat that has a coat featuring distinctive stripes, dots, lines or swirling patterns, usually with a mark resembling an 'M' on its forehead."
---

## How To # 1:

### List running services:

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

#### [Back](./notes-0001.md)
