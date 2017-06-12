---
external help file: AIP.dll-Help.xml
ms.assetid: 76192204-7E23-467D-B3FA-7A697F06CFB3
online version: 
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
The Clear-AIPAuthentication cmdlet clears the authentication token and RMS templates within the “msip” store for the current user.

This cmdlet applies to AIP applications only and does not affect protection templates inside Office.

## EXAMPLES

### Example 1
```
PS C:\> Clear-AIPAuthentication
Cleared credentials
```

This command clears the currently cached authentication token for a user who is authenticated to AIP..

## PARAMETERS

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

