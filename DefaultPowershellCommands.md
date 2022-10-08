# Default Powershell Commands

PowerShell utilizes cmdlets, which are small single-function tools built into the shell.
Cmdlets are in the form of Verb-Noun.

Cmdlets also take arguments or flags. We can type `Verb-Noun -` and hit the tab key to iterate through the arguments.

## Get Help on Commands

> Get-Help commandName

## Aliases

> Get-Alias

## OS Info

> wmic os list brief

> Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber

## Directories

> dir c:\ /a

## File Structure

> tree c:\ /f | more

## Integrity Control Access Control List

> icacls c:\windows

> icacls c:\users /grant joe:f

> icacls c:\users /remove joe.

## List Services

> Get-Service serviceName

> Get-Service | ? {$_.Status -eq "Running"} | select -First 2 |fl

## Examine / Start / Stop Services

_The sc.exe command can just be run as sc in a Command Prompt._

> sc.exe qc serviceName

> sc.exe //hostnameOrIp serviceName

> Stop-Service serviceName

> Start-Service serviceName

> sc.exe sdshow wuauserv

Result:

```
D:(A;;CCLCSWRPLORC;;;AU)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;SY)
```

This amalgamation of characters crunched together and delimited by opened and closed parentheses is in a format known as
the Security Descriptor Definition Language (SDDL).

We may be tempted to read from left to right because that is how the English language is typically written,
but it can be much different when interacting with computers. Read the entire security descriptor for the
Windows Update (wuauserv) service in this order starting with the first letter and set of parentheses:

```
D: (A;;CCLCSWRPLORC;;;AU)
```

D: - the proceeding characters are DACL permissions

AU: - defines the security principal Authenticated Users

A;; - access is allowed

CC - SERVICE_QUERY_CONFIG is the full name, and it is a query to the service control manager (SCM) for the service
configuration

LC - SERVICE_QUERY_STATUS is the full name, and it is a query to the service control manager (SCM) for the current
status of the service

SW - SERVICE_ENUMERATE_DEPENDENTS is the full name, and it will enumerate a list of dependent services

RP - SERVICE_START is the full name, and it will start the service

LO - SERVICE_INTERROGATE is the full name, and it will query the service for its current status

RC - READ_CONTROL is the full name, and it will query the security descriptor of the service

_As we read the security descriptor, it can be easy to get lost in the seemingly random order of characters, but recall
that we are essentially viewing access control entries in an access control list. Each set of 2 characters in between
the semicolons represents actions allowed to be performed by a specific user or group._

```
;;CCLCSWRPLORC;;;
```

After the last set of semicolons, the characters specify the security principal (User and/or Group) that is permitted
to perform those actions.

```
;;;AU
```

The character immediately after the opening parentheses and before the first set of semicolons defines whether the
actions are Allowed or Denied.

```
A;;
```

This entire security descriptor associated with the Windows Update (wuauserv) service has three sets of access control
entries because there are three different security principals. Each security principal has specific permissions applied.

### Examine Service Permissions the PowerShell Way

> Get-ACL -Path HKLM:\System\CurrentControlSet\Services\wuauserv | Format-List

_This returns specific account permissions in an easy-to-read format._

### Create User

> net user /add name pass

### Get SID for All Users

> wmic useraccount get name,sid

### Create Group

> net localgroup HR /add

### Get SID for All Groups

> wmic group get name,sid

