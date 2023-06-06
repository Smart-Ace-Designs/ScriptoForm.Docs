---
Tag: region, main
---
# Main Region
The **Main** region is used to call the script block which displays the [[Forms#Forms Region|main form]].  This region may perform other duties, depending on the function of the ScriptoForm, such as checking for the presence of required PowerShell modules before the main form is displayed or closing sessions to remote systems after the main form has closed.

The region is denoted with the "#region Main" tag and occurs after the [[Handlers|Handlers]] region in the ScriptoForm script.
## Code Example
```powershell
#region Main
Invoke-Command -ScriptBlock $ShowFormMain
#endregion
```