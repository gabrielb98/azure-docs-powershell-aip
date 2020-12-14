---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 91DD14FF-0033-4A7F-9738-87BD2A989FED
online version: https://go.microsoft.com/fwlink/?linkid=2044860
schema: 2.0.0
---

# Disconnect-AipService

## SYNOPSIS
Disconnects from Azure Information Protection.

## SYNTAX

```
Disconnect-AipService [<CommonParameters>]
```

## DESCRIPTION
The **Disconnect-AipService** cmdlet disconnects you from the protection service from Azure Information Protection. Use this cmdlet to end a connection that you previously established by using the [Connect-AipService](./Connect-AipService.md) cmdlet.

## EXAMPLES

### Example 1: Disconnect from Azure Information Protection
```
PS C:\>Disconnect-AipService
```

This command disconnects you from the protection service from Azure Information Protection.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Connect-AipService](./Connect-AipService.md)