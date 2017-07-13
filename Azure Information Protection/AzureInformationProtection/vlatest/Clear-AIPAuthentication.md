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
The Clear-AIPAuthentication cmdlet deletes the cached authentication for the current user, so that this account is no longer authenticated for Azure Information Protection.

In addition, all Rights Management templates from the %LocalAppData%\Microsoft\MSIPC\msip folder are deleted for the current user. Rights Management templates are not deleted from the %LocalAppData\Microsoft\MSIPC folder that Office uses.


## EXAMPLES

### Example 1
```
PS C:\> Clear-AIPAuthentication
Cleared credentials
```

This command removes stored authentication for Azure Information Protection and deletes Rights Management templates for the current user.


## PARAMETERS

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

[Set-AIPAuthentication](./Set-AIPAuthentication.md)
