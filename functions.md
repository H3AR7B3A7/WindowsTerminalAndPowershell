# Additional PowerShell Functions
These can be added to the 'profile', find location by using following command:
>$Profile

If you haven't used it before we will have to create the file. The profile path will likely look like this:
For the default Powershell:
C:\Users\<UserName>\Documents\WindowsPowerShell

For Powershell 7:
C:\Users\<UserName>\Documents\PowerShell

	# Shorten the current directory path to just the folder
    function prompt{
      $check = $pwd.drive
      if ( "$check`:\" -eq $pwd.path){
        "$pwd>"
      }else{
        $p = Split-Path -leaf -path (Get-Location)
        "~ \$p> $"
      }
    }
    
    # Change or create files
    function touch {
      Param(
        [Parameter(Mandatory=$true)]
        [string]$Path
      )
    
      if (Test-Path -LiteralPath $Path) {
        (Get-Item -Path $Path).LastWriteTime = Get-Date
      } else {
        New-Item -Type File -Path $Path
      }
    }
    
    # Encode
    function encode([string]$arg){
    	[Convert]::ToBase64String([System.Text.Encoding]::UTF8.GetBytes($arg))
    }
    
    # Decode
    function decode([string]$arg) {
    	[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($arg))
    }