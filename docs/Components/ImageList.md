---
tag: code, example, component, dotnet
---
# ImageList Component
In a [[Index|ScriptoForm]], an **ImageList** component is used to manage a collection of [Image](https://learn.microsoft.com/en-us/dotnet/api/system.drawing.image?view=windowsdesktop-7.0) objects.  An **ImageList** is typically used by other controls, such as the [ListView](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.listview?view=windowsdesktop-7.0), [TreeView](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.treeview?view=windowsdesktop-7.0), or [ToolBar](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.toolbar?view=windowsdesktop-7.0). You can add bitmaps or icons to the **ImageList**, and the other controls are able to use the images as they require.
## Examples
```powershell
# Create the ImageList and assign properties:
$ImageListMain = New-Object -TypeName System.Windows.Forms.ImageList
$ImageListMain.TransparentColor = [Drawing.Color]::Transparent
$ImageListMain.ColorDepth = [System.Windows.Forms.ColorDepth]::Depth32Bit
$ImageListMain.ImageSize = New-Object -TypeName System.Drawing.Size(32,32)

# Add files to the ImageList:
$ImageListMain.Images.Add([Drawing.Image]::FromFile($ToolPNGFile))
$ImageListMain.Images.Add([Drawing.Image]::FromFile($ScriptICOFile))
foreach ($IconFile in Get-ChildItem $CustomIconsLocation)
{ 
	$ImageListMain.Images.Add($IconFile.BaseName,[System.Drawing.Icon]::ExtractAssociatedIcon($IconFile.FullName))
}

# Assign the ImageList to a control:
$ListViewMain.LargeImageList = $ImageListMain
```
## Notes
The above code example shows how to use an **ImageList** component to store images for use by a [[ListView|ListView]] control.
## References
[ImageList Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.imagelist?view=windowsdesktop-7.0)