---
tag: code, example, control, dotnet
---
# DateTimePicker Control
A **DateTimePicker** control allows the user to select a date and a time and in a specified format, which can be used to determine various actions performed by a ScriptoForm.

![[DateTimePicker1.png]] ![[DateTimePicker2.png]]

In the ScriptoForm PowerShell script file, a DateTimePicker control should be instantiated in the [Controls](app://obsidian.md/Controls) region and then defined within the [main forms](app://obsidian.md/Forms) script block. If using the VS Code snippets file, the *Controls: Label & DateTimePicker* snippet can be used to instantiate a default DateTimePicker and [Label](app://obsidian.md/Label) pair in the script and the *Properties: Label & DateTimePicker* snippet can be used to assign a default set of properties to them.

Designing the functionality and behavior of a DateTimePicker within a ScriptoForm might include:

- The initial date\time value in a DateTimePicker can be set by using the `Text` property
- The value of the date\time in a DateTimePicker can be obtained from the `Text` property
- A minimum date\time in a DateTimePicker can be enforced by using the `MinDate` property
- The format of the date\time in a DateTimePicker can be controlled by using the `Format` and `CustomFormat` properties

## Examples
Instantiate a control pair:
```powershell
#region Controls
$LabelDate = New-Object -TypeName System.Windows.Forms.Label
$DateTimePickerDate = New-Object -TypeName System.Windows.Forms.DateTimePicker
#endregion
```

Set properties on a control pair:
```powershell
$DateTimePickerDate.Location = New-Object -TypeName System.Drawing.Point(15,145)
$DateTimePickerDate.Size = New-Object -TypeName System.Drawing.Size(($FormWidth - 50),20)
$DateTimePickerDate.TabIndex = 2
$DateTimePickerDate.Format = [System.Windows.Forms.DateTimePickerFormat]::Custom
$DateTimePickerDate.CustomFormat = "MM/dd/yyyy"
$DateTimePickerDate.MinDate = [System.DateTime]::Today
$DateTimePickerDate.Text = ((Get-Date).AddDays(1)).ToString("MM/dd/yyyy")
$GroupBoxMain.Controls.Add($DateTimePickerDate)
```

Select date value of a DateTimePicker:
```powershell
$RestartDate = $DateTimePickerDate.Text
```
## Notes
In the above example, the DateTimePicker control only selects a date and uses a "Month(2)/Day(2)/Year(4)" format.
## References
[DateTimePicker Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.datetimepicker?view=windowsdesktop-7.0)