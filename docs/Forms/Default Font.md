---
tag: code, example, form, dotnet, font
---
# Default Font
In a [[Index|ScriptoForm]], starting with PowerShell 7, the default font size and family have changed and no longer match what was used with previous versions (Windows PowerShell).  This is due to changes in the .NET framework used by PowerShell 7.  This can be changed back to the original font by setting the ``Font`` property of the form object.
## Examples:
```powershell
$FormMain.Font = New-Object -TypeName System.Drawing.Font("MS Sans Serif",8)
```
## Notes
Some child controls of the form may not inherit this property and will require the value to be set separately at the control level.
## References
[Default font changes](https://learn.microsoft.com/en-us/dotnet/desktop/winforms/whats-new/net60?view=netdesktop-6.0#change-the-default-font)
