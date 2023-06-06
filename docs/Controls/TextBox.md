---
alias: TextBox
tag: code, example, control, dotnet
---
# TextBox Control
In a [[Index|ScriptoForm]], a **TextBox** control allows the user to provide text or numerical data to the underlying script.

![[TextBox.png]]
## Examples
A basic TextBox control:
```powershell
$TextBoxName = New-Object -TypeName System.Windows.Forms.TextBox

$TextBoxName.Location = New-Object -TypeName System.Drawing.Point(15,35)
$TextBoxName.Size = New-Object -TypeName System.Drawing.Size(($FormWidth - 50),20)
$TextBoxName.TabIndex = 0
$TextBoxName.Add_TextChanged($TextBoxName_TextChanged)
$GroupBoxMain.Controls.Add($TextBoxName)

$TextBoxName_TextChanged =
{
    if ($TextBoxName.TextLength -eq 0)
    {
        $ErrorProviderMain.Clear()
        $ButtonRun.Enabled = $false
    }
    else
    {
        $ErrorProviderMain.Clear()
        $ButtonRun.Enabled = $true
    }
}
```
Enforcing upper case characters:
```powershell
$TextBoxName.CharacterCasing = [System.Windows.Forms.CharacterCasing]::Upper
```
Highlight specific text when a TextBox receives focus:
```powershell
$TextBoxEmail.Add_GotFocus($TextBoxEmail_GotFocus)

$TextBoxEmail_GotFocus =
{
    if ($TextBoxEmail.TextLength -ne 0)
    {
        try
        {
            $EmailDomainName = (New-Object -TypeName MailAddress($TextBoxEmail.Text)).Host
            $TextBoxEmail.SelectionStart = 0
            $TextBoxEmail.SelectionLength = ($TextBoxEmail.TextLength - ($EmailDomainName.Length + 1))
        }
        catch {$TextBoxEmail.SelectionStart = 0}
    }
}

# Alternate method:
$TextBoxParameters.Add_GotFocus($TexBoxParmameters_GotFocus)

$TexBoxParmameters_GotFocus =
{
    $TextBoxParameters.SelectionStart = 20
    $TextBoxParameters.SelectionLength = 10
}
```
## Notes
A **TextBox** control is normally paired with a [[Label|Label]] control.

## References
[TextBox Class (System.Windows.Forms) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.textbox?view=windowsdesktop-7.0)