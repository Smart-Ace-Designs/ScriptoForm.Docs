---
tag: code, example, form, dotnet
---
# Assembly
An **Assembly** is a collection of types and resources that are built to work together and form a logical unit of functionality.  In a [[Index|ScriptoForm]], assemblies are used to implement Windows forms and child controls and components.  They can be referenced by using the `Add-Type` cmdlet, which lets you define a Microsoft .NET class in your PowerShell session available in the referenced assembly.  You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET object.
## Examples
```powershell
Add-Type -AssemblyName System.Windows.Forms

# Other lesser used assemblies:
Add-Type -AssemblyName System.Windows.Forms.DataVisualization
Add-Type -AssemblyName System.Drawing
Add-Type -AssemblyName System.Data
Add-Type -AssemblyName System.Xml
```
## Notes
An **Assembly** must be loaded **prior** to instantiating any form or control defined in it.
## References
[Assemblies in .NET | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/standard/assembly/)
[Add-Type (Microsoft.PowerShell.Utility) - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7.3)