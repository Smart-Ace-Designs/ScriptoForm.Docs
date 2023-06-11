---
tag: code, example, control, dotnet
---
# DataGridView Control
A **DataGridView** control is used to provide a customizable and sortable table for displaying data to the user.

![[DataGridView.png]]

In the ScriptoForm PowerShell script file, a ComboBox control should be instantiated in the [[Controls]] region and then defined within the [[Forms|main forms]] script block.  The data (such as an array of objects) should first be converted  into a *System.Data.DataTable* .NET object type when used with a **DataGridView** control [^1] so that it can be sorted interactively.

> Note: There is not currently a PowerShell snippet available for adding a DataGridView control to a ScriptoForm.
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

Function used to convert an array of objects to a System.Data.DataTable object:
```powershell
function ConvertTo-DataTable
{
    [OutputType([System.Data.DataTable])]
    param
    (
        [ValidateNotNull()] $ObjectArray
    )

    $DataTable = New-Object -TypeName System.Data.DataTable
    $DataTable.Clear()

    if ($ObjectArray.GetType() -eq [System.Object[]])
    {
        foreach ($Property in $ObjectArray[0].PSObject.Get_Properties())
        {
            [void]$DataTable.Columns.Add($Property.Name)
        }

        $DataTable.Rows.Clear()
        foreach ($Item in $ObjectArray)
        {
            $Row = $DataTable.NewRow()
            if ($Item)
            {
                foreach ($Property in $Item.PSObject.Get_Properties())
                {
                    if ($DataTable.Columns.Contains($Property.Name))
                    {
                        $Row.Item($Property.Name) = $Property.Value
                    }
                }
            }
            [void]$DataTable.Rows.Add($Row)
        }
        return @(,$DataTable)
    }
}

# ConvertTo-DataTable function example
$Processes = Get-Process | Select-Object @{N = "Process Name";E = {$PSItem.ProcessName}},@{N = "Process Identifier";E = {$PSItem.Id}} | Sort-Object "Process Name"
$DataGridViewProcesses.DataSource = ConvertTo-DataTable -ObjectArray $Processes
```
## Notes
The above example shows how to convert an array of ServiceController objects into a *System.Data.DataTable* .NET object type and set that as the data source for the **DataGridView** object.  The `ConvertTo-DataTable` function may not be suitable for arrays of other types.
## References
[DataGridView Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.datagridview?view=windowsdesktop-7.0)
[DataTable Class (System.Data) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.data.datatable?view=net-7.0)

[^1]: [PowerShell Studio: Working with the DataGridView Control – SAPIEN Blog](https://www.sapien.com/blog/2020/09/08/powershell-studio-working-with-the-datagridview-control/)