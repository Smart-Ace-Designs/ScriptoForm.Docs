---
tag: code, example, component, dotnet
---
# ErrorProvider Component
In a [[Index|ScriptoForm]], an **ErrorProvider** component provides a user interface for indicating that a control on a form has an error associated with it or to notify the user of a data entry error.  This normally manifests itself in the form of a red "X" icon in the vicinity of the control in a error state that includes a tooltip that provides a customizable error message.  A single **ErrorProvider** component can be used with multiple controls on a form.

![[ErrorProvider.png]]
## Examples
```powershell
# Create the ErrorProvider:
$ErrorProviderMain = New-Object -TypeName System.Windows.Forms.ErrorProvider

# Display error icon with custom error message if invalid data detected:
$ErrorProviderMain.SetIconPadding($TextBoxName,-20)
$ErrorProviderMain.SetError($TextBoxName,"Error message.")

# Clear error icon if valid data detected:
$ErrorProviderMain.Clear()
```
## Notes
The above example shows how to display the error icon within the control text region instead of outside of it by using a **negative** parameter value in the *SetIconPadding* method.
## References
[ErrorProvider Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.errorprovider?view=windowsdesktop-7.0)