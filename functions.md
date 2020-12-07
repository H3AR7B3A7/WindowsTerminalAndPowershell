# Additional PowerShell Functions
These can be added to the 'profile', find location by using following command:
>$Profile

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

	function encode([string]$arg){
		[Convert]::ToBase64String([System.Text.Encoding]::UTF8.GetBytes($arg))
	}

	function decode([string]$arg) {
		[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($arg))
	}