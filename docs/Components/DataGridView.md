---
tag: code, example, component, dotnet
---
# DataGridView Component
In a [[Index|ScriptoForm]], a **DataGridView** control is used to provide a customizable table for displaying data.  The data (such as an array of objects) should first be converted  into a *System.Data.DataTable* .NET object type when used with a **DataGridView** control [^1] so that it can be sorted interactively.

![[DataGridView.png]]
## Examples
```powershell
$DataGridViewProcesses = New-Object -TypeName System.Windows.Forms.DataGridView

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

# Example Use:
$Processes = Get-Process | Select-Object @{N = "Process Name";E = {$PSItem.ProcessName}},@{N = "Process Identifier";E = {$PSItem.Id}} | Sort-Object "Process Name"
$DataGridViewProcesses.DataSource = ConvertTo-DataTable -ObjectArray $Processes
```
## Notes
The above example shows how to convert an array specifically of ServiceController objects into a _System.Data.DataTable_ .NET object type and set that as the data source for the **DataGridView** object.  The `ConvertTo-DataTable` function may not be suitable for arrays of other types.
## References
[DataGridView Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.datagridview?view=windowsdesktop-7.0)

[^1]: [PowerShell Studio: Working with the DataGridView Control – SAPIEN Blog](https://www.sapien.com/blog/2020/09/08/powershell-studio-working-with-the-datagridview-control/)