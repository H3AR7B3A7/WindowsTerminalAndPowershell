# Installing Powershell

## Using Installer

Download the installer [here](https://github.com/PowerShell/PowerShell) and follow the instructions.


## Using Commandline

> iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"

You can also use other installation parameters:
- Destination – change the default PowerShell Core installation directory
- Preview – install the latest Preview PowerShell version
- Quiet – a quiet installation
- AddToPath – adds a path to the PowerShell Core installation directory to the environment variables
update powershell core 7.1 from command line


## Using Chocolatey

If you have Chocolatey package manager installed, you can install or update your PowerShell version using the following commands:

> choco install powershell -y

> choco upgrade powershell -y