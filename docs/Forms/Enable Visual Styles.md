---
tag: code, example, form, dotnet
---
# Enable Visual Styles
In a [[Index|ScriptoForm]], the **EnableVisualStyles** static .NET function enables visual styles for the application.  Visual styles are the colors, fonts, and other visual elements that form an operating system theme. This function gives the controls used in a script a more modern and aesthetically pleasing appearance.
## Examples
```powershell
Add-Type -AssemblyName System.Windows.Forms
[System.Windows.Forms.Application]::EnableVisualStyles()
```
## Notes
The "EnableVisualStyles" function is defined in the "System.Windows.Forms" namespace and must be called after loading the [[Assembly|assembly]] for it.  To have an effect, this function must be called before instantiating any controls objects.
## References
[Application.EnableVisualStyles Method (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.application.enablevisualstyles?view=windowsdesktop-7.0)
