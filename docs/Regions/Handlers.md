---
Tag: region, handlers
---
# Handlers Region
The **Handlers** [[Regions|region]] is used to define all form, component, and control event handlers, which are script blocks that are executed when an event is raised.  Examples of events include clicking a button, typing text into a textbox, and showing a form.

The region is denoted with the "#region Handlers" tag and occurs between the [[Functions|Functions]] and [[Main|Main]] regions in the ScriptoForm script.
## Code Example
```powershell
#region Handlers
$FormMain_Shown =
{
    $ToolStripStatusLabelMain.Text = "Ready"
    $StatusStripMain.Update()
    $FormMain.Activate()
}

<#
Add event handlers here...
#>

$ButtonRun_Click =
{
    $ToolStripStatusLabelMain.Text = "Working...please wait"
    $FormMain.Controls | Where-Object {$PSItem -isnot [System.Windows.Forms.StatusStrip]} | ForEach-Object {$PSItem.Enabled = $false}
    $FormMain.Cursor = [System.Windows.Forms.Cursors]::WaitCursor
    [System.Windows.Forms.Application]::DoEvents()

    try
    {
        <#
        Do work here...
        #>
    }
    catch
    {
        <#
        Add custom exception handling here...
        #>
        [void][System.Windows.Forms.MessageBox]::Show(
	        $PSItem.Exception.Message + "`n`nPlease contact $SupportContact for technical support.",
	        "Exception",
	        [System.Windows.Forms.MessageBoxButtons]::OK,
	        [System.Windows.Forms.MessageBoxIcon]::Warning
		)
    }

    $FormMain.Controls | ForEach-Object {$PSItem.Enabled = $true}
    $FormMain.ResetCursor()
    <#
    Reset controls here...
    #>
    $ToolStripStatusLabelMain.Text = "Ready"
    $StatusStripMain.Update()
}
#endregion
```
## References
[Event Handlers Overview - Windows Forms .NET Framework | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/desktop/winforms/event-handlers-overview-windows-forms?view=netframeworkdesktop-4.8)