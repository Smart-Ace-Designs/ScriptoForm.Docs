---
Tag: region, functions
---
# Functions Region
The **Functions** region is used define all PowerShell functions that are used throughout the ScriptoForm script.  If not functions are used within the ScriptoForm, this region can be removed from the script file.

This region is denoted with the "#region Functions" tag and occurs between the [[Forms|Forms]] and [[Handlers|Handlers]] regions in the ScriptoForm script.
## Code Example
```powershell
#region Functions
function Import-ExchangeCommands
{
    param
    (
        [Parameter(Mandatory = $true,Position = 0)] [string]$MailServer,
        [Parameter(Mandatory = $true,Position = 1)] [string[]]$ExchangeCommands,
        [Parameter(Mandatory = $false,Position = 2)] [string]$CertificateFriendlyName
    )

    $Certificate = Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object FriendlyName -eq $CertificateFriendlyName
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "http://$MailServer/powershell/?SerializationLevel=Full" -Authentication Kerberos -ErrorAction Stop
    if ($Certificate) {Import-PSSession -Session $Session -Certificate $Certificate -DisableNameChecking -CommandName $ExchangeCommands -FormatTypeName *}
    else {Import-PSSession -Session $Session -DisableNameChecking -CommandName $ExchangeCommands -FormatTypeName *}
}

<#
Add function definitions here...
#>
#endregion
```