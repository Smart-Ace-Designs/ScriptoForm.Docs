---
tag: code, example, control, dotnet
---
# ListView Control
In a [[Index|ScriptoForm]], a **ListView** control is used to display a collection of items represented by icons and/or text.  These items can be interactive giving you the ability to double-click an item to perform an action within the ScriptoForm.  Items with a **ListView** can be divided in to separate groups by using a [ListViewGroup](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.listviewgroup?view=windowsdesktop-7.0) object to group items by a useful category.

![[ListView.png]]

## Examples
```powershell
$ListViewItems = New-Object -TypeName System.Windows.Forms.ListView
$ListViewGroupTools = New-Object -TypeName System.Windows.Forms.ListViewGroup
$ListViewGroupScripts = New-Object -TypeName System.Windows.Forms.ListViewGroup

$ListViewItems.Anchor = "Top,Bottom,Left,Right"
$ListViewItems.MultiSelect = $false
$ListViewItems.ContextMenuStrip = $ContextMenuStripListView
$ListViewItems.LabelWrap = $false
$ListViewItems.LargeImageList = $ImageList
$ListViewItems.Location = New-Object -TypeName System.Drawing.Point(13,15)
$ListViewItems.Size = New-Object -TypeName System.Drawing.Size((430 + $FormWidthOffset),(347 + $FormHeightOffset))
$ListViewItems.Sorting = [System.Windows.Forms.SortOrder]::Ascending
$ListViewItems.TabIndex = 0
$ListViewItems.View = [System.Windows.Forms.View]::Tile
$ListViewItems.Add_DoubleClick($ListViewItems_DoubleClick)
$ListViewItems.Add_Click($ListViewItems_Click)
$ListViewItems.Add_MouseDown($ListViewItems_MouseDown)
$FormMain.Controls.Add($ListViewItems)

$ListViewGroupTools.Header = "Tools"
[void]$ListViewItems.Groups.Add($ListViewGroupTools)

$ListViewGroupScripts.Header = "Scripts"
[void]$ListViewItems.Groups.Add($ListViewGroupScripts)
```
## Notes
Starting with Microsoft .NET 5, the ability to collapse/expand a **ListView** group was added as well as several other [useful features](https://devblogs.microsoft.com/dotnet/whats-new-in-windows-forms-runtime-in-net-5-0/#listview-enhancements).
## References
[ListView Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.listview?view=windowsdesktop-7.0)