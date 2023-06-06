---
tag: code, example, control, dotnet
---
# Label Control
In a [[Index|ScriptoForm]], a **Label** control is used to provide descriptive text for another control on the Windows form. For example, you can use a **Label** to add descriptive text for a [[TextBox|TextBox]] control to inform the user about the type of data expected in the control.

![[Label.png]]
## Examples
```powershell
$LabelName = New-Object -TypeName System.Windows.Forms.Label

$LabelName.Location = New-Object -TypeName System.Drawing.Point(15,15)
$LabelName.AutoSize = $true
$LabelName.Text = "Group Name:"
$GroupBoxMain.Controls.Add($LabelName)
```
## Notes
A **Label** control is usually paired with another control such as a [[TextBox|TextBox]] or ComboBox.
## References
[Label Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.label?view=windowsdesktop-7.0)