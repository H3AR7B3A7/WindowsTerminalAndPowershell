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

FAT32 (File Allocation Table), where 32 refers to the fact that FAT32 uses 32 bits of data for identifying data clusters on a storage device.

- Pros of FAT32:

  - Device compatibility - it can be used on computers, digital cameras, gaming consoles, smartphones, tablets, and more.
  - Operating system cross-compatibility - It works on all Windows operating systems starting from Windows 95 and is also
  supported by MacOS and Linux.


- Cons of FAT32:

  - Can only be used with files that are less than 4GB.
  - No built-in data protection or file compression features.
  - Must use third-party tools for file encryption.

### NTFS

NTFS (New Technology File System) is the default Windows file system since Windows NT 3.1.
In addition to making up for the shortcomings of FAT32, NTFS also has better support for metadata and better performance due to improved data structuring.

- Pros of NTFS:

  - NTFS is reliable and can restore the consistency of the file system in the event of a system failure or power loss.
  - Provides security by allowing us to set granular permissions on both files and folders.
  - Supports very large-sized partitions.
  - Has journaling built-in, meaning that file modifications (addition, modification, deletion) are logged.

- Cons of NTFS:

  - Most mobile devices do not support NTFS natively.
  - Older media devices such as TVs and digital cameras do not offer support for NTFS storage devices.

_The NTFS file system has many basic and advanced permissions:_

- Full control
- Modify
- List Folder Contents
- Read & Execute
- Write
- Read
- Traverse folder

