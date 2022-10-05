# Default Powershell Commands

## Get Help on Commands

> Get-Help commandName

## OS Info

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

> Get-Service | ? {$_.Status -eq "Running"} | select -First 2 |fl
