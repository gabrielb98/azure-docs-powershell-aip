---
external help file: AIP.dll-Help.xml
ms.assetid: 76192204-7E23-467D-B3FA-7A697F06CFB3
online version: https://go.microsoft.com/fwlink/?linkid=851287
schema: 2.0.0
---

# Clear-AIPAuthentication

## SYNOPSIS
Clears the authentication token and RMS templates for the current user.

## SYNTAX

```
Clear-AIPAuthentication
```

## DESCRIPTION
The **Clear-AIPAuthentication** cmdlet resets the user settings for the Azure Rights Management service. For a list of files and registry entries that are deleted, see [More information about the Reset Settings option](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide#more-information-about-the-reset-settings-option) in the admin guide.

In addition, all Rights Management templates from the %LocalAppData%\Microsoft\MSIPC\msip folder are deleted for the current user. Rights Management templates are not deleted from the %LocalAppData\Microsoft\MSIPC folder that Office uses.

## EXAMPLES

### Example 1
```
PS C:\> Clear-AIPAuthentication

```

This command is functionally the equivalent of selecting the **Reset Settings** from the Help and Feedback menu option, and deleting the templates.


## PARAMETERS

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Set-AIPAuthentication](./Set-AIPAuthentication.md)
