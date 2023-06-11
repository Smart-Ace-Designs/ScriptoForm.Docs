---
tag: code, example, control, dotnet
---
# DataGridView Control
A **DataGridView** control is used to provide a customizable and sortable table for displaying data to the user.

![[DataGridView.png]]

In the ScriptoForm PowerShell script file, a ComboBox control should be instantiated in the [[Controls]] region and then defined within the [[Forms|main forms]] script block.

## Examples
Instantiate a DataGridView control:
```powershell
$DataGridViewProcesses = New-Object -TypeName System.Windows.Forms.DataGridView
```

Set properties on a DataGridView control:
```powershell
$DataGridViewProcesses.Location = New-Object -TypeName System.Drawing.Point(15,35)
$DataGridViewProcesses.Size = New-Object -TypeName System.Drawing.Size(($FormWidth - 50),325)
$DataGridViewProcesses.TabStop = $false
$DataGridViewProcesses.RowTemplate.Height = 20
$DataGridViewProcesses.DataBindings.DefaultDataSourceUpdateMode = [System.Windows.Forms.DataSourceUpdateMode]::OnValidation
$DataGridViewProcesses.ScrollBars = [System.Windows.Forms.ScrollBars]::Vertical
$DataGridViewProcesses.RowHeadersVisible = $false
$DataGridViewProcesses.AllowUserToResizeRows = $false
$DataGridViewProcesses.ReadOnly = $true
$DataGridViewProcesses.AllowUserToAddRows = $false
$DataGridViewProcesses.AllowUserToDeleteRows = $false
$GroupBoxMain.Controls.Add($DataGridViewProcesses)
```

## Notes
The data used with a **DataGridView** control should first be converted  into a *System.Data.DataTable* .NET object type so that it can be sorted interactively.

## References
[DataGridView Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.datagridview?view=windowsdesktop-7.0)
[DataTable Class (System.Data) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.data.datatable?view=net-7.0)
