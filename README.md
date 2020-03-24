# ultimate-windows-speedup-guide

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

## Disable AppXSvc 
1. HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\AppXSvc
2. In the right panel, change the value of Start to 4.

## Disable SysMain service
1. services.msc > SysMain > Properties > Disable 

## Disable Microsoft Office Click-to-Run service
1. services.msc > Microsoft Office Click-to-Run > Properties > Disable 

## Disable startup apps 
1. ...from Task Manager

## Turn off Background Apps
1. Background apps > Prevent apps from running in background (fret not..all are just useless apps)
