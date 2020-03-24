# ultimate-windows-speedup-guide

## Automated for noobs 
https://github.com/10se1ucgo/DisableWinTracking

## Disable windows automatic update
1. Download script windows-update.ps1
2. Open powershell with elevated privileges.
3. Run
```
Set-ExecutionPolicy RemoteSigned
& "~\Desktop\windows-update.ps1"
```

## Disable Windows Store
1. Create key `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\WindowsStore`
2. Create new DWORD value within the Windows Store key and name it `RemoveWindowsStore` and give it the value of ‘1’.

## Disable Windows Compatibility Telemetry
In elevated cmd,
1. sc delete DiagTrack
2. sc delete dmwappushservice
3. echo ““ > C:\ProgramData\Microsoft\Diagnosis\ETLLogs\AutoLogger\AutoLogger-DiagTrack-Listener.etl
In regedit,
HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Data Collection
create a new DWORD of 32-bit and name it as AllowTelemetry and then assign it a 0 value.


## Disable AppXSvc 
1. HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\AppXSvc
2. In the right panel, change the value of Start to 4.

## Disable following services
1. services.msc > ?? > Properties > Disable 
### List
1. Windows Search
2. Windows Update
3. SysMain 
4. Microsoft Office Click-to-Run 

## Disable startup apps 
1. ...from Task Manager

## Turn off Background Apps
1. Background apps > Prevent apps from running in background (fret not..all are just useless apps)

## Lenovo specific
Uninstall apps 
1. Host app Service Updater
2. Cyberlink *

Have more time?
https://www.marksanborn.net/howto/turn-off-unnecessary-windows-services/
