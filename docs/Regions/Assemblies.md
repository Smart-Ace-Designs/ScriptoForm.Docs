---
Tag: region, assemblies
---
# Assemblies Region
The **Assemblies** [[Regions|region]] is used to load the "System.Windows.Forms" [[Assembly|Assembly]] to the ScriptoForm with the [Add-Type](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7.3) cmdlet.  This allows for .NET forms and controls to be used with the script.  This assembly must be loaded prior to instantiating any form or control.

This region is denoted with the "#region Assemblies" tag and occurs between the [[Settings|Settings]] and [[Appearance|Appearance]] regions in a ScriptoForm script.
## Examples
```powershell
#region Assemblies
Add-Type -AssemblyName System.Windows.Forms
#endregion
```
## References
[Assemblies in .NET | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/standard/assembly/)