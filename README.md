# ultimate-windows-speedup-guide

## Tips
1. Run a command as administrator from RUN (Ctrl+R), using `Ctrl+Shift+Enter`.

## Install gpedit.msc
Download and run as administrator. Logs generated in List.txt   
**BONUS:** To update the changes made in gpedit, do in cmd `gpupdate /force`

## Automated for noobs 
https://github.com/10se1ucgo/DisableWinTracking

## Take a look here
https://github.com/Sycnex/Windows10Debloater

## Disable windows automatic update
1. gpedit.msc
```
Computer Configuration\Administrative Templates\Windows Components\Windows Update
```
OR
1. Download script windows-update.ps1
2. Open powershell with elevated privileges.
3. Run
```
Set-ExecutionPolicy RemoteSigned
& "~\Desktop\windows-update.ps1"
```

## Disable Windows Defender
1. gpedit.msc 
```
Computer Configuration/Administrative Templates/Windows Components/Windows Defender Antivirus/Real-time Protection
```
OR
1. In cmd(admin)
```
REG ADD “hklmsoftwarepoliciesmicrosoftwindows defender” /v DisableAntiSpyware /t REG_DWORD /d 1 /f
```
## Disable onedrive
1. gpedit
```
Computer Configuration > Administrative Templates > Windows Components > OneDrive > Prevent the usage of OneDrive for file storage
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
