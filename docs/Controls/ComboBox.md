---
tag: code, example, control, dotnet
---
# ComboBox Control
A **ComboBox** control allows a user to interactively select one of multiple items from a drop-down style list, which can be used to determine various actions performed by a ScriptoForm.

![[ComboBox.png]]

In the ScriptoForm PowerShell script file, a ComboBox control should be instantiated in the [[Controls]] region and then defined within the [[Forms|main forms]] script block.  If using the VS Code snippets file, the *Controls: Label & ComboBox* snippet can be used to instantiate a default ComboBox and [[Label]] pair in the script and the *Properties: Label & ComboBox* snippet can be used to assign a default set of properties to them.

Designing the functionality and behavior of a ComboBox within a ScriptoForm might include:

- Items can be pre-added to a ComboBox during the `OnLoad()` event of the main form and added or removed during runtime as required
- Actions can be performed when trigged by the `SelectedIndexChanged()` event of a ComboBox
- The value of the selected text in a ComboBox can be obtained by using the `.Text` property of a ComboBox

## Examples
Instantiate a control pair:
```powershell
#region Controls
$LabelEnvironment = New-Object -TypeName System.Windows.Forms.Label
$ComboBoxEnvironment = New-Object -TypeName System.Windows.Forms.ComboBox
#endregion
```

Set properties on a control pair:
```powershell
#region Forms
$ShowFormMain =
{
	# ...
	$LabelEnvironment.Location = New-Object -TypeName System.Drawing.Point(15,70)
    $LabelEnvironment.AutoSize = $true
    $LabelEnvironment.Text = "Environment:"
    $GroupBoxMain.Controls.Add($LabelEnvironment)
    
    $ComboBoxEnvironment.Location = New-Object -TypeName System.Drawing.Point(15,90)
    $ComboBoxEnvironment.Size = New-Object -TypeName System.Drawing.Size(($FormWidth - 50),20)
    $ComboBoxEnvironment.TabIndex = 1
    $ComboBoxEnvironment.DropDownStyle = [System.Windows.Forms.ComboBoxStyle]::DropDownList
    $ComboBoxEnvironment.Add_SelectedIndexChanged($ComboBoxEnvironment_SelectedIndexChanged)
    $GroupBoxMain.Controls.Add($ComboBoxEnvironment)
	# ...
}
#endregion
```

Add items to a ComboBox:
```powershell
$FormMain_Load =
{
    if (Test-Path -Path $EnvironmentsFile)
    {
        $ComboBoxEnvironment.Items.AddRange($(Get-Content -Path $EnvironmentsFile))
        $ComboBoxEnvironment.SelectedIndex = 0
    }
}
```

Select text value of a ComboBox:
```powershell
$Environment = $ComboBoxEnvironment.Text
```
## Notes
The "DropDownStyle" property of a ComboBox determines one of three [ComboBoxStyle](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.comboboxstyle?view=windowsdesktop-7.0#fields) behaviors the ComboBox will exhibit.  Typically, in a ScriptoForm, the `DropDownList` style is used, which indicates the list is non-interactive and cannot be modified by the user.

## References
[ComboBox Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.combobox?view=windowsdesktop-7.0)