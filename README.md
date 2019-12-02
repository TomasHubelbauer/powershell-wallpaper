# Powershell Wallpaper

Set the desktop wallpaper using PowerShell:

```powershell
# Using PowerShell to write to the  registry
set-itemproperty -path "HKCU:Control Panel\Desktop" -name WallPaper -value "%UserProfile%\Desktop\wallpaper.jpg"
# Using `reg`
reg add "HKEY_CURRENT_USER\Control Panel\Desktop" /v WallPaper /t REG_SZ /d "%UserProfile%\Desktop\wallpaper.jpg" /f
```

Clear the desktop wallpaper using PowerShell:

```powershell
# Using PowerShell to write to the  registry
set-itemproperty -path "HKCU:Control Panel\Desktop" -name WallPaper -value ""
# Using `reg`
reg add "HKEY_CURRENT_USER\Control Panel\Desktop" /v WallPaper /t REG_SZ /d "" /f
```

## Refreshing

The registry write will not have an immediate effect on the desktop background.
It is necessary to initiate a per user settings reload:

```powershell
RUNDLL32.EXE USER32.DLL, UpdatePerUserSystemParameters
```

## Resources

https://docs.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-systemparametersinfoa

## To-Do

### Hook into an event indicating `UpdatePerUserSystemParameters` completion

This will ensure the call went through successfully and will enable to hold the script until it does.

### Add working scripts for setting the desktop background color
