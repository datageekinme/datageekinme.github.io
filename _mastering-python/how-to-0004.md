---
title: "Using Powershell"
permalink: /mastering-python/how-to-0004/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 255, 0, 0.5)
classes: wide
excerpt: "How-To #4: Creating a file in Windows using Powershell"
---

# Creating a file in Windows using Powershell

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
