## How To # 2:

### Creating directories recursively:

The following option can be used in all operating systems, be it MacOS, Windows (using Powershell) or Linux.

The below snippet shows an example using Powershell on Windows:

`pwd` gives the present working directory on the terminal.

```powershell
pwd
```
![current working directory](../Images/how-to-0002-ss-001.JPG)

Below command helps in creating another directory in the present working directory.

```powershell
 mkdir testdir
```

![creating a directory](../Images/how-to-0002-ss-002.JPG)

Following code snippet shows the option of creating sub-directories recursively using the `mkdir -p` option:


```powershell
mkdir -p .\testdir\subdir1\sub-subdir1
```

![creating directories recursively](../Images/how-to-0002-ss-003.JPG)

#### [Back](./notes-0001.md)
