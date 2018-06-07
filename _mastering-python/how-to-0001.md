---
title: "Using Powershell"
permalink: /mastering-python/how-to-0001/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/how-to-1.jpg"
toc: true
value: "b"
excerpt: "A collection of How-To's for Using Powershell"
---

## How-To #1: List running services

### Windows:
The below command lists all the sevices that are currently running on a Windows PC using Powershell:

```powershell
Get-Service | Where-Object {$_.Status –eq “Running”}
```

### MacOS:
On a MacOS, the following command can be used on a terminal:

```terminal
ps aux
```

The above command lists all the services. To list only specific services, we can use the below command

```terminal
ps aux | grep <process-name>
```

`<process-name>` needs to be replaced with the process that you are looking for.

## How-To #2: Creating directories recursively

The following option can be used in all operating systems, be it MacOS, Windows (using Powershell) or Linux.

The below snippet shows an example using Powershell on Windows:

`pwd` gives the present working directory on the terminal.

```powershell
pwd
```
![current working directory](/assets/images/courses/mastering-python/how-to-0002-ss-001.JPG){: .align-center}

Below command helps in creating another directory in the present working directory.

```powershell
 mkdir testdir
```

![creating a directory](/assets/images/courses/mastering-python/how-to-0002-ss-002.JPG){: .align-center}

Following code snippet shows the option of creating sub-directories recursively using the `mkdir -p` option:


```powershell
mkdir -p .\testdir\subdir1\sub-subdir1
```

![creating directories recursively](/assets/images/courses/mastering-python/how-to-0002-ss-003.JPG){: .align-center}

## How-To #3: Listing directories recursively

The following option can be used in all operating systems, be it MacOS, Windows (using Powershell) or Linux.

The below snippet shows how to list directories recursively using the `-R` option of the `ls` command:

```powershell
ls -R
```

![listing directories recursively](/assets/images/courses/mastering-python/how-to-0003-ss-001.JPG){: .align-center}

## How-To #4: Creating a file in Windows using Powershell

There are 2 options to creating a file using powershell:

1. Using the `echo` command:

      ```powershell
      echo $null >> test-file.py
      ```

      ![Create file using echo](/assets/images/courses/mastering-python/how-to-0004-ss-001.JPG){: .align-center}

      The caveat using the above command is that, it creates a file with UTF-16 encoding. Python requires UTF-8 encoded files to run.

2. Using the `New-Item` command:

      ```powershell
      New-Item -ItemType file test-file-alt.py
      ```

      ![Create file using New-Item](/assets/images/courses/mastering-python/how-to-0004-ss-002.JPG){: .align-center}

[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
