# Windows Terminal Settings

Other shells that were added include: PowerShell 7, Git Bash, Python, JShell
These tools and/or languages will have to be installed separately.

- [Powershell 7](https://github.com/PowerShell/PowerShell)
- [Git Bash](https://git-scm.com/downloads)
- [Python Shell](https://www.python.org/downloads/)
- [JShell](https://www.oracle.com/java/technologies/javase-downloads.html)

To start your terminal elevated from your taskbar just create a shortcut with the following as location:

	C:\Windows\System32\cmd.exe /c start /b wt

Icons modified to make your terminal look better, are provided in the [img](https://github.com/H3AR7B3A7/WindowsTerminalAndPowershell/tree/master/img) folder of this repository as well.

### Settings

	{
	  "$schema": "https://aka.ms/terminal-profiles-schema",

	  "defaultProfile": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",

	  // You can add more global application settings here.
	  // To learn more about global settings, visit https://aka.ms/terminal-global-settings

	  // If enabled, selections are automatically copied to your clipboard.
	  "copyOnSelect": false,

	  // If enabled, formatted data is also copied to your clipboard
	  "copyFormatting": false,

	  // A profile specifies a command to execute paired with information about how it should look and feel.
	  // Each one of them will appear in the 'New Tab' dropdown,
	  //   and can be invoked from the commandline with `wt.exe -p xxx`
	  // To learn more about profiles, visit https://aka.ms/terminal-profile-settings
	  "profiles": {
		"defaults": {
		  // Put settings here that you want to apply to all profiles.
		  "acrylicOpacity": 0.5,
		  "useAcrylic": true,
		  "colorScheme": "Tango Dark",
		  "backgroundImage": "C:\\Users\\Admin\\Pictures\\Saved Pictures\\terminalBG.png",
		  "backgroundImageOpacity": 0.5,
		  "padding": "0, 0, 0, 0",
		  "closeOnExit": true,
		  "fontFace": "Consolas",
		  "fontSize": 12,
		  "cursorShape": "bar",
		  "cursorColor": "#FFFFFF",
		  "snapOnInput": true,
		  "historySize": 9001,
		  "startingDirectory": "C:\\" //"%USERPROFILE%"
		},
		"list": [
		  {
			// Make changes here to the POWERSHELL 7 profile.
			"tabTitle": "POWERSHELL",
			"guid": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",
			"hidden": false,
			"name": "PowerShell 7",
			"commandline": "pwsh.exe -NoLogo",
			"source": "Windows.Terminal.PowershellCore"
		  },
		  {
			// Make changes here to the OLD POWERSHELL profile.
			"tabTitle": "POWERSHELL (OLD)",
			"guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
			"name": "PowerShell (OLD)",
			"commandline": "powershell.exe -NoLogo",
			"hidden": false
		  },
		  {
			// Make changes here to the CMD profile.
			"tabTitle": "CMD",
			"guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
			"name": "Command Prompt",
			"commandline": "cmd.exe",
			"hidden": false
		  },
		  {
			// Make changes here to the AZURE CLOUD SHELL profile.
			"tabTitle": "AZURE CLOUD",
			"guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
			"name": "Azure Cloud Shell",
			"hidden": false,
			"source": "Windows.Terminal.Azure"
		  },
		  {
			// Make changes here to the GIT BASH profile.
			"tabTitle": "GIT BASH",
			"guid": "{00000000-0000-0000-0000-000000012345}",
			"name": "Git Bash",
			"commandline": "\"%PROGRAMFILES%\\git\\bin\\bash.exe\" --login -i -l",
			"icon": "%PROGRAMFILES%/git/mingw64/share/git/git-for-windows.ico"
		  },
		  {
			// Make changes here to the Python Shell
			"tabTitle": "PYTHON",
			"guid": "{1850e97f-16dc-4281-9ea9-0100c4e852c5}",
			"commandline": "py.exe",
			"icon": "C:/Users/Admin/AppData/Local/Programs/Python/Python38/Lib/test/imghdrdata/python.png",
			"name": "Python"
		  },
		  {
			// Make changes here to the JShell
			"tabTitle": "JSHELL",
			"guid": "{e1840119-35c4-4dcc-a456-ecdf38222fa0}",
			"commandline": "jshell.exe",
			"icon": "C:\\Users\\Admin\\Pictures\\Saved Pictures\\java.png",
			"name": "JShell"
		  }
		]
	  },

	  // Add custom color schemes to this array.
	  // To learn more about color schemes, visit https://aka.ms/terminal-color-schemes
	  "schemes": [
		{
		  "background": "#000000",
		  "black": "#0C0C0C",
		  "blue": "#6060ff",
		  "brightBlack": "#767676",
		  "brightBlue": "#3B78FF",
		  "brightCyan": "#61D6D6",
		  "brightGreen": "#16C60C",
		  "brightPurple": "#B4009E",
		  "brightRed": "#E74856",
		  "brightWhite": "#F2F2F2",
		  "brightYellow": "#F9F1A5",
		  "cyan": "#3A96DD",
		  "foreground": "#bfbfbf",
		  "green": "#00a400",
		  "name": "GitBash",
		  "purple": "#bf00bf",
		  "red": "#bf0000",
		  "white": "#ffffff",
		  "yellow": "#bfbf00",
		  "grey": "#bfbfbf"
		}
	  ],

	  // Add custom keybindings to this array.
	  // To unbind a key combination from your defaults.json, set the command to "unbound".
	  // To learn more about keybindings, visit https://aka.ms/terminal-keybindings
	  "keybindings": [
		// Copy and paste are bound to Ctrl+Shift+C and Ctrl+Shift+V in your defaults.json.
		// These two lines additionally bind them to Ctrl+C and Ctrl+V.
		// To learn more about selection, visit https://aka.ms/terminal-selection
		{
		  "command": {
			"action": "copy",
			"singleLine": false
		  },
		  "keys": "ctrl+c"
		},
		{
		  "command": "paste",
		  "keys": "ctrl+v"
		},

		// Press Ctrl+Shift+F to open the search box
		{
		  "command": "find",
		  "keys": "ctrl+shift+f"
		},

		// Press Alt+Shift+D to open a new pane.
		// - "split": "auto" makes this pane open in the direction that provides the most surface area.
		// - "splitMode": "duplicate" makes the new pane use the focused pane's profile.
		// To learn more about panes, visit https://aka.ms/terminal-panes
		{
		  "command": {
			"action": "splitPane",
			"split": "auto",
			"splitMode": "duplicate"
		  },
		  "keys": "alt+shift+d"
		}
	  ]
	}