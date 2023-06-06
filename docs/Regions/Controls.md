---
Tag: region, controls
---
# Controls Region
The **Controls** region is used to instantiate the child [[Control-vs-Component|control and component]] objects of the form.  This typically includes buttons, textboxes, labels, and combo boxes.  These classes are defined in the "System.Windows.Forms" .NET namespace, and must be instantiated after that assembly has been loaded.

This region is denoted with the "#region Controls" tag and must occur between the [[Appearance|Appearance]] [^Note] and [[Forms|Forms]] regions in a ScriptoForm script.
## Code Example
```powershell
#region Controls
$FormMain = New-Object -TypeName System.Windows.Forms.Form
$GroupBoxMain = New-Object -TypeName System.Windows.Forms.GroupBox
$LabelServerName = New-Object -TypeName System.Windows.Forms.Label
$TextBoxServerName = New-Object -TypeName System.Windows.Forms.TextBox
$ButtonRun = New-Object -TypeName System.Windows.Forms.Button
$ButtonClose = New-Object -TypeName System.Windows.Forms.Button
$StatusStripMain = New-Object -TypeName System.Windows.Forms.StatusStrip
$ToolStripStatusLabelMain = New-Object -TypeName System.Windows.Forms.ToolStripStatusLabel
$ErrorProviderMain = New-Object -TypeName System.Windows.Forms.ErrorProvider
#endregion
```
## Notes
Although called **Controls**, this region can contain both components and controls.  Although a control is type of component, it is more typically found in this region due to its graphical nature, and hence that name that is used.

[^Note]:  Changes with .NET 6 and newer:
	Starting with Microsoft .NET 6, the "EnableVisualStyles()" static function, located in the [[Appearance|Appearance]] region, must be called before controls are instantiated in order for visual styles to work.  Prior to this version, the function could be called anywhere within the script below the loading of the "System.Windows.Forms" namespace assembly.