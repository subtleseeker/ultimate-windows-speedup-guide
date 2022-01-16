# ultimate-windows-speedup-guide

Activate windows/office: https://github.com/massgravel/Microsoft-Activation-Scripts
Disable updates: https://github.com/DavidXanatos/wumgr   
Debloater: https://github.com/Sycnex/Windows10Debloater   
Antispyware: https://www.oo-software.com/en/shutup10    

---
Note: The remaining stuff is old, before I knew better.   

Check this out: https://superuser.com/questions/404617/what-is-the-proper-way-of-debugging-a-slow-windows-installation

## Tips
1. Run a command as administrator from RUN (Ctrl+R), using `Ctrl+Shift+Enter`.
2. Restarting in safe mode: 
```
bcdedit /set {current} safeboot network
shutdown /r
```
To disable it back, (yeah you need to disable it)
```
bcdedit /deletevalue {current} safeboot
shutdown /r
```
3. Process Explorer: http://live.sysinternals.com/procexp.exe   

## Block windows update completely with host file
Append to c:\Windows\System32\Drivers\etc\hosts after getting ownership of the file.
```
########################
# Block windows update
########################
127.0.0.1 *.download.windowsupdate.com
127.0.0.1 *.microsoft.com
127.0.0.1 *.update.microsoft.com
127.0.0.1 *.windowsupdate.com
127.0.0.1 *.windowsupdate.microsoft.com
127.0.0.1 download.microsoft.com
127.0.0.1 download.windowsupdate.com
127.0.0.1 ntservicepack.microsoft.com
127.0.0.1 test.stats.update.microsoft.com
127.0.0.1 windowsupdate.microsoft.com
127.0.0.1 wustat.windows.com
127.0.0.1 stats.microsoft.com
```

## Disable Anti-malware service
1. Regedit `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender`, maybe take permission of dir.    
2. Set `DisableAntiSpyware` and `DisableAntiVirus` both to 1.   


## Disable Windows Update
1. Regedit `HKEY\LOCAL\MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU`, set `NoAutoUpdate` to 1
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`, create a DWORD `DisableAntiSpyware` and set it to 1, and `AUOptions` to 2 (notify to download and install updates).   

## Install gpedit.msc
Download and run as administrator. Logs generated in List.txt   
**BONUS:** To update the changes made in gpedit, do in cmd `gpupdate /force`

## Install sysinternals
1. Install sysinternals suite
2. Install psexec and run regedit with more permissions from cmd: `psexec -s -i regedit`

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
