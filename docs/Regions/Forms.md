---
Tag: region, forms
---
# Forms Region
The **Forms** [[Regions|region]] is used to define the script block for each Windows form used in the ScriptoForm script.  Each script block performs the following actions for it's respective form:

- Sets the form properties and declares [[Handlers|Event Handlers]] for the form
- For each child control/component that will exist in the form, sets the properties and declares [[Handlers|Event Handlers]] for it
- Calls the "ShowDialog()" method to display the form
- After the form has closed, calls the "Dispose()" method to dispose of the resource used by the form

Each ScriptoForm script should include at least one form script block which is used to show the main form for the ScriptoForm.  This script block is typically named "$ShowFormMain".

This region is denoted with the "#region Forms" tag and must occur between the [[Controls|Controls]] and [[Functions|Functions]] regions in a ScriptoForm script.
## Examples
```powershell
#region Forms
$ShowFormMain =
{
    $FormWidth = 330
    $FormHeight = 260
    
    $FormMain.Icon = [System.Drawing.Icon]::ExtractAssociatedIcon((Get-Process -Id $PID).Path)
    $FormMain.Text = "Title"
    $FormMain.Font = New-Object -TypeName System.Drawing.Font("MS Sans Serif",8)
    $FormMain.ClientSize = New-Object -TypeName System.Drawing.Size($FormWidth,$FormHeight)
    $FormMain.StartPosition = [System.Windows.Forms.FormStartPosition]::CenterScreen
    $FormMain.FormBorderStyle = [System.Windows.Forms.FormBorderStyle]::FixedSingle
    $FormMain.MaximizeBox = $false
    $FormMain.AcceptButton = $ButtonRun
    $FormMain.CancelButton = $ButtonClose
    $FormMain.Add_Shown($FormMain_Shown)

    $GroupBoxMain.Location = New-Object -TypeName System.Drawing.Point(10,5)
    $GroupBoxMain.Size = New-Object -TypeName System.Drawing.Size(($FormWidth - 20),($FormHeight - 80))
    $FormMain.Controls.Add($GroupBoxMain)

    <#
    Assign control properties, event handlers, and containment here...
    #>

    $ButtonRun.Location = New-Object -TypeName System.Drawing.Point(($FormWidth - 175),($FormHeight - 60))
    $ButtonRun.Size = New-Object -TypeName System.Drawing.Size(75,25)
    $ButtonRun.TabIndex = 100
    $ButtonRun.Enabled = $false
    $ButtonRun.Text = "Run"
    $ButtonRun.Add_Click($ButtonRun_Click)
    $FormMain.Controls.Add($ButtonRun)

    $ButtonClose.Location = New-Object -TypeName System.Drawing.Point(($FormWidth - 85),($FormHeight - 60))
    $ButtonClose.Size = New-Object -TypeName System.Drawing.Size(75,25)
    $ButtonClose.TabIndex = 101
    $ButtonClose.Text = "Close"
    $ButtonClose.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
    $FormMain.Controls.Add($ButtonClose)

    $StatusStripMain.SizingGrip = $false
    $StatusStripMain.Font = New-Object -TypeName System.Drawing.Font("MS Sans Serif",8)
    [void]$StatusStripMain.Items.Add($ToolStripStatusLabelMain)
    $FormMain.Controls.Add($StatusStripMain)

    [void]$FormMain.ShowDialog()
    $FormMain.Dispose()
}
#endregion
```