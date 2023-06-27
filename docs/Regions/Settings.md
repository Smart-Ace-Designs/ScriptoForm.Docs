---
Tag: region, settings, constants
---
# Settings Region
The **Settings** [[Regions|region]] is used to declare PowerShell constant variables ("settings") that are used throughout the ScriptoForm script.  These usually represent unique values specific to your corporate environment, such as a specific DNS server IP address or Active Directory domain name, that will rarely or never change.  This region may also contain other constants specific to the script itself such as timeout values or fixed lists.  This region should never contain calculated or derived values.

This region is denoted with the "#region Settings" tag and usually occurs between the [[Header|Header]] and the [[Assemblies|Assemblies]] regions in a ScriptoForm script.
## Code Example
```powershell
#region Settings
$DNSServer = "10.10.10.1"
$DomainName = "CORP.PRI"
$SupportContact = "FirstName LastName"
#endregion
```