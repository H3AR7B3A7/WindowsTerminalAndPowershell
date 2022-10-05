# Windows

## Remote Access

- Virtual Private Networks (VPN)
- Secure Shell (SSH)
- File Transfer Protocol (FTP)
- Virtual Network Computing (VNC)
- Windows Remote Management (or PowerShell Remoting) (WinRM)
- Remote Desktop Protocol (RDP)

### RDP

_RDP listens by default on logical port 3389.
By default, remote access is not allowed on Windows operating systems._

If we are connecting to a Windows target from a Windows host,
we can use the built-in RDP client application called Remote Desktop Connection
([mstsc.exe](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/mstsc)).

Remote Desktop Connection also allows us to save connection profiles.
As pentesters, we can benefit from looking for these saved Remote Desktop Files (.rdp) while on an engagement.

## File Systems

### FAT32

FAT32 (File Allocation Table), where 32 refers to the fact that FAT32 uses 32 bits of data for identifying data clusters
on a storage device.

- Pros of FAT32:

    - Device compatibility - it can be used on computers, digital cameras, gaming consoles, smartphones, tablets, and
      more.
    - Operating system cross-compatibility - It works on all Windows operating systems starting from Windows 95 and is
      also
      supported by MacOS and Linux.


- Cons of FAT32:

    - Can only be used with files that are less than 4GB.
    - No built-in data protection or file compression features.
    - Must use third-party tools for file encryption.

### NTFS

NTFS (New Technology File System) is the default Windows file system since Windows NT 3.1.
In addition to making up for the shortcomings of FAT32, NTFS also has better support for metadata and better performance
due to improved data structuring.

- Pros of NTFS:

    - NTFS is reliable and can restore the consistency of the file system in the event of a system failure or power
      loss.
    - Provides security by allowing us to set granular permissions on both files and folders.
    - Supports very large-sized partitions.
    - Has journaling built-in, meaning that file modifications (addition, modification, deletion) are logged.

- Cons of NTFS:

    - Most mobile devices do not support NTFS natively.
    - Older media devices such as TVs and digital cameras do not offer support for NTFS storage devices.

#### Permissions

The Server Message Block protocol (SMB) is used in Windows to connect shared resources like files and printers.

Share permissions and NTFS basic permissions are not the same but often apply to the same shared resource.

Share permissions:

- Full control
- Change
- Read

NTFS basic permissions:

- Full control
- Modify
- List Folder Contents
- Read & Execute
- Write
- Read

NTFS special permissions:

- Full control
- Traverse folder / execute file
- List folder/read data
- Read attributes
- Read extended attributes
- Create files/write data
- Create folders/append data
- Write attributes
- Write extended attributes
- Delete sub-folders and files
- Delete
- Read permission
- Change permission
- Take ownership

### Computer Management

Computer Management is a tool we can use to identify and monitor shared resources on a Windows system.

### Event Viewer

Event Viewer is another good place to investigate actions completed on Windows.

### Service Control Manager (SCM)

Windows services are managed via the Service Control Manager system, accessible via the services.msc MMC add-in.

It is also possible to query and manage services via the command line using sc.exe using PowerShell cmdlets such as
Get-Service.

> Get-Service | ? {$_.Status -eq "Running"} | select -First 2 |fl

_If we update any file or resource in use by a critical system services, we must restart the system._

### Local Security Authority Subsystem Service (LSASS)

lsass.exe is the process that is responsible for enforcing the security policy on Windows systems.
When a user attempts to log on to the system, this process verifies their log on attempt and creates
access tokens based on the user's permission levels.

### Sysinternals Tools

The SysInternals Tools suite is a set of portable Windows applications that can be used to administer Windows systems
(for the most part without requiring installation).

> \\live.sysinternals.com\tools\procdump.exe -accepteula

Some tools in this suite:

- Process Explorer, an enhanced version of Task Manager
- Process Monitor, used to monitor file system, registry, and network activity related to any process running on the
  system.
- TCPView, used to monitor internet activity
- PSExec, used to manage/connect to systems via the SMB protocol remotely.

