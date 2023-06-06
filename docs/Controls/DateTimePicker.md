---
tag: code, example, control, dotnet
---
# Title
In a [[Index|ScriptoForm]], a **DateTimePicker** control allows the user to select a date and a time and in a specified format.

![[DateTimePicker1.png]] ![[DateTimePicker2.png]]
## Examples
A basic DateTimePicker control that only selects a date and uses a "Month(2)/Day(2)/Year(4)" format:
```powershell
$DateTimePickerDate = New-Object -TypeName System.Windows.Forms.DateTimePicker

$DateTimePickerDate.Location = New-Object -TypeName System.Drawing.Point(15,145)
$DateTimePickerDate.Size = New-Object -TypeName System.Drawing.Size(($FormWidth - 50),20)
$DateTimePickerDate.TabIndex = 2
$DateTimePickerDate.Format = [System.Windows.Forms.DateTimePickerFormat]::Custom
$DateTimePickerDate.CustomFormat = "MM/dd/yyyy"
$DateTimePickerDate.MinDate = [System.DateTime]::Today
$DateTimePickerDate.Text = ((Get-Date).AddDays(1)).ToString("MM/dd/yyyy")
$GroupBoxMain.Controls.Add($DateTimePickerDate)
```
## Notes
A **DateTimePicker** control is normally paired with a [[Label|Label]] control.
## References
[DateTimePicker Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.datetimepicker?view=windowsdesktop-7.0)