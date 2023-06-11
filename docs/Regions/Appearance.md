---
Tag: region, appearance
---
# Appearance Region
The **Appearance** region is used to call the "EnableVisualStyles" static .NET function which enables visual styles for the application - no other code should exist in this region.  Visual styles provides a modern and aesthetically pleasing appearance, that matches operating system theme, to the ScriptoForm.  The "EnableVisualStyles" function is defined in the "System.Windows.Forms" namespace and must be called after loading the assembly for it.

This region is denoted with the "#region Appearance" tag and occurs between the [[Controls|Assemblies]] and [[Controls|Controls]] regions in a ScriptoForm script.
## Examples
```powershell
#region Appearance
[System.Windows.Forms.Application]::EnableVisualStyles()
#endregion
```
## References
[Application.EnableVisualStyles Method (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.application.enablevisualstyles?view=windowsdesktop-7.0)