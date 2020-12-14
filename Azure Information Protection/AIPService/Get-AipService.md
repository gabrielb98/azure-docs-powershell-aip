---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: DF116EAD-6AC1-44CF-89E6-5E63D72FF58C
online version: https://go.microsoft.com/fwlink/?linkid=2044945
schema: 2.0.0
---

# Get-AipService

## SYNOPSIS
Gets the activation status of the protection service from Azure Information Protection.

## SYNTAX

```
Get-AipService [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipService** cmdlet gets the activation status of the protection service from Azure Information Protection for your tenant. The status of the protection service is enabled (activated) or disabled (deactivated).

You can also view this information in a management portal. For more information, see [Activating the protection service from Azure Information Protection](/information-protection/deploy-use/activate-service).

## EXAMPLES

### Example 1: Get the status of the protection service
```
PS C:\>Get-AipService
```

This command gets your tenant's activation status of the protection service from Azure Information Protection.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipService](./Disable-AipService.md)

[Enable-AipService](./Enable-AipService.md)