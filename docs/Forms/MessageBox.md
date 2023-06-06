---
tag: code, example, form, dotnet
---
# MessageBox
In a [[Index|ScriptoForm]], a **MessageBox** displays a message window, also known as a dialog box, which presents a message to the user.  For example, the ScriptoForm may use a **MessageBox** to notify the user that action has completed or that an error has occurred.

![[MessageBox.png]]

## Examples
```powershell
Add-Type -AssemblyName System.Windows.Forms
[System.Windows.Forms.Application]::EnableVisualStyles()

# Show informational icon
[void][System.Windows.Forms.MessageBox]::Show(
	"This is a test.",
	"Title",
	[System.Windows.Forms.MessageBoxButtons]::OK,
	[System.Windows.Forms.MessageBoxIcon]::Information
)

# Show warning icon
[void][System.Windows.Forms.MessageBox]::Show(
	"This is a test.",
	"Title",
	[System.Windows.Forms.MessageBoxButtons]::OK,
	[System.Windows.Forms.MessageBoxIcon]::Warning
)
```
## Notes
The ``System.Windows.Forms`` [[Assembly|assembly]] must be loaded prior to using a **MessageBox**.
## References
[MessageBox Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.messagebox?view=windowsdesktop-7.0)