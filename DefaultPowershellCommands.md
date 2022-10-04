# Default Powershell Commands

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

