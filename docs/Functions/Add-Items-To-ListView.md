---
alias: Add Items to ListView
tag: code, example, function, dotnet
---
# Add Items to a ListView
In a [ScriptoForm](app://obsidian.md/Info.ScriptoForms), items can be added to a [[ListView|ListView]] object using a special function developed by SAPIEN Technologies [^1].
## Examples:
```powershell
function Add-ListViewItem
{
    <#
    .SYNOPSIS
        Adds the item to the ListView and stores the object in the ListViewItem's Tag property.
        
        Note:
        This function is written and provided by Sapien Technologies; it was modified to eliminate unused features.
    .DESCRIPTION
        Adds the item to the ListView and stores the object in the ListViewItem's Tag property.
    .PARAMETER ListView
        The ListView control to add the items to.
    .PARAMETER Items
        The object you wish to load into the ListView's Items collection.
    .PARAMETER  ImageIndex
        The index of a predefined image in the ListView's ImageList.
    .PARAMETER  SubItems
        List of strings to add as Subitems.
    .PARAMETER Group
        The group to place the item(s) in.
    .PARAMETER Clear
        This switch clears the ListView's Items before adding the new item(s).
    .EXAMPLE
        Add-ListViewItem -ListView $listview1 -Items "Test" -Group $listview1.Groups[0] -ImageIndex 0
    #>
    
    Param( 
    [ValidateNotNull()]
    [Parameter(Mandatory=$true)]
    [System.Windows.Forms.ListView]$ListView,
    [ValidateNotNull()]
    [Parameter(Mandatory=$true)]
    $Items,
    [int]$ImageIndex = -1,
    $Group)
    
    $LVGroup = $null
    if ($Group -is [System.Windows.Forms.ListViewGroup])
    {
        $LVGroup = $Group
    }
    elseif ($Group -is [string])
    {
        foreach ($GroupItem in $ListView.Groups)
        {
            if ($GroupItem.Name -eq $Group)
            {
                $LVGroup = $GroupItem
                break
            }
        }
        if ($LVGroup -eq $null)
        {
            $LVGroup = $ListView.Groups.Add($Group, $Group)
        }
    }
    $ListItem  = $ListView.Items.Add($Items.Name.ToString(), $ImageIndex)
    $ListItem.Tag = $Items
    if($LVGroup -ne $null)
    {
        $ListItem.Group = $LVGroup
    }
}

# Example use:
$Tools = Import-Clixml "$ScriptDirectory\Tools.xml"
foreach ($Tool in $Tools)
{
    Add-ListViewItem -ListView $ListView -Items $Tool -Group "listviewgroup1" -ImageIndex 1
}
```
## Notes
The above function is a customized version of the original that eliminates unused parts and is more suitable for use with ScriptoForms.

[^1]: [Spotlight on the ListView Control – Part 1 – SAPIEN Blog](https://www.sapien.com/blog/2012/04/04/spotlight-on-the-listview-control-part-1/)