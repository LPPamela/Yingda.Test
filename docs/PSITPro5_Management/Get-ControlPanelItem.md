﻿# Get-ControlPanelItem

## SYNOPSIS
Gets control panel items.

## DESCRIPTION
The Get-ControlPanelItem cmdlet gets control panel items on the local computer.
You can use it to find control panel items by name, category, or description, even on systems that do not have a user interface.

Get-ControlPanelItem gets only the control panel items that can be opened on the system.
On computers that do not have Control Panel or File Explorer, Get-ControlPanelItem gets only control panel items that can open without these components.

This cmdlet is introduced in Windows PowerShell 3.0.
It works only on Windows 8 and Windows Server 2012.

## PARAMETERS

### CanonicalName [String[]]

```powershell
[Parameter(
  Mandatory = $true,
  ParameterSetName = 'Set 2')]
```

Gets control panel items with the specified canonical names or name patterns.
Wildcards are permitted.
If you enter multiple names, Get-ControlPanelItem gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.

By default, Get-ControlPanelItem gets all control panel items in the system.


### Category [String[]]

Gets control panel items in the specified categories.
Enter a category name or name pattern.
Wildcards are permitted.
If you enter multiple names, Get-ControlPanelItem gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.
By default, Get-ControlPanelItem gets all control panel items in the system.


### InformationAction [System.Management.Automation.ActionPreferencering[]]

```powershell
[ValidateSet(
  'SilentlyContinue',
  'Stop',
  'Continue',
  'Inquire',
  'Ignore',
  'Suspend')]
```


By default, Get-ControlPanelItem gets all control panel items in the system.


### InformationVariable [System.Stringring[]]


By default, Get-ControlPanelItem gets all control panel items in the system.


### Name [String[]]

```powershell
[Parameter(
  Position = 1,
  ValueFromPipeline = $true,
  ValueFromPipelineByPropertyName = $true,
  ParameterSetName = 'Set 1')]
```

Gets control panel items with the specified names or name patterns.
Wildcards are permitted.
You can also pipe a name or name pattern to the Get-ControlPanelItem cmdlet.



## INPUTS
### System.String

You can pipe a name or name pattern to the Get-ControlPanelItem cmdlet.

## OUTPUTS
### Microsoft.PowerShell.Commands.ControlPanelItem




## EXAMPLES
### Example 1: Get all control panel items

```powershell
PS C:\>Get-ControlPanelItem
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and... 
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s... 
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo... 
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin... 
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana... 
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden... 
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...

```
This command gets all control panel items on the local computer.


### Example 2: Get control panel items by name

```powershell
PS C:\>Get-ControlPanelItem –Name *program*, *app*

```
This command gets control panel items that have "program" or "app"  in their names.


### Example 3: Get control panel items by category

```powershell
PS C:\>Get-ControlPanelItem –Category *security*


```
This command gets all control panel items in categories that have "Security" in their names.


### Example 4: Open a control panel item

```powershell
PS C:\>Get-ControlPanelItem –Name "Windows Firewall" | Show-ControlPanelItem


```
This command opens the Windows Firewall control panel item on the local computer.
It uses the Get-ControlPanelItem cmdlet to get the control panel item and the Show-ControlPanelItem cmdlet to open it.


### Example 5: Get control panel items on a remote computer

```powershell
PS C:\>Invoke-Command –ComputerName Server01 {Get-ControlPanelItem –Name "BitLocker*" }


```
This command gets the  BitLocker Drive Encryption control panel item on the Server01 remote computer.
It uses the Invoke-Command cmdlet to run the Get-ControlPanelItem cmdlet remotely.


### Example 6: Search the descriptions of control panel items

```powershell
PS C:\>Get-ControlPanelItem | Where-Object {$_.Description -like "*device*"}
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo... 
Devices and Printers          Microsoft.DevicesAndPrinters  {Hardware}                    View and manage devices, p... 
Sound                         Microsoft.Sound               {Hardware}                    Configure your audio devic...

```
This command searches the Description property of the control panel item objects and gets only those that contain "device".
The command uses the Get-ControlPanelItem cmdlet to get all control panel items and the Where-Object cmdlet to filter the items by the value of the Description property.



## RELATED LINKS

[Online Version:](http://go.microsoft.com/fwlink/p/?linkid=290492)

[Show-ControlPanelItem]()

