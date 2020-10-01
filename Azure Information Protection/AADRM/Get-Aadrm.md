---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400606
schema: 2.0.0
ms.assetid: DF116EAD-6AC1-44CF-89E6-5E63D72FF58C
---

# Get-Aadrm

## SYNOPSIS
Gets the activation status of Rights Management for your organization.

## SYNTAX

```
Get-Aadrm [<CommonParameters>]
```

## DESCRIPTION
[!INCLUDE [AADRM is deprecated](../includes/aadrm-deprecated.md)]

The **Get-Aadrm** cmdlet gets the activation status of Azure Rights Management for your organization. The status of Rights Management is enabled (activated) or disabled (deactivated).

You can also view this information in a management portal. For more information, see [Activating the protection service from Azure Information Protection](/information-protection/deploy-use/decommission-deactivate).

## EXAMPLES

### Example 1: Get the status of Rights Management
```
PS C:\>Get-Aadrm
```

This command gets the activation status of your Rights Management service for your organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-Aadrm](./Disable-Aadrm.md)

[Enable-Aadrm](./Enable-Aadrm.md)