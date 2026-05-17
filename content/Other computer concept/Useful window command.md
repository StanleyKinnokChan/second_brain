---
title: Useful window command
tags:
  - concepts
---
Battery report
```
powercfg /batteryreport
./battery-report.html
```

Delete a folder that contain large amount of files
```
mkdir \empty
robocopy /mir \empty <folder>
```

SMART Status check (Self-Monitoring, Analysis, and Reporting Technology of drives)

```
wmic diskdrive get model,status
```

Scan the corrupted file and replace with cached ones
```
sfc /scannow
DISM /Online /Cleanup-Image /CheckHealth
DISM /Online /Cleanup-Image /ScanHealth
DISM /Online /Cleanup-Image /RestoreHealth
```

See system info
```
window+r
msinfo32
```

Quick access in folder explorer
```
%userprofile% or .s
%temp%
%appdata%
%localappdata%
```

open software using admin
```
right click, then ctrl + shift + enter
```

create an empty file
```
type NUL > filename.txt
```

show file structure
```
cd ./path
tree /f
```