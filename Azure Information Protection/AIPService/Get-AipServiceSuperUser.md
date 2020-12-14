---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 508FBF5B-A405-4FCB-9EB3-39183F46F60A
online version: https://go.microsoft.com/fwlink/?linkid=2045209
schema: 2.0.0
---

# Get-AipServiceSuperUser

## SYNOPSIS
Gets the super users for Azure Information Protection.

## SYNTAX

```
Get-AipServiceSuperUser [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceSuperUser** cmdlet gets the super users for Azure Information Protection, who can unprotect or protect files for your organization when the super user feature is enabled by using the [Enable-AipServiceSuperUserFeature](./Enable-AipServiceSuperUserFeature.md) cmdlet.

You must use PowerShell to configure super users; you cannot do this configuration by using a management portal.

For more information about super users, see [Configuring super users for Azure Information Protection and discovery services or data recovery](/information-protection/deploy-use/configure-super-users).

## EXAMPLES

### Example 1: List super users
```
PS C:\>Get-AipServiceSuperUser
```

This command lists the super users for Information Protection.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md)

[Remove-AipServiceSuperUser](./Remove-AipServiceSuperUser.md)

[Enable-AipServiceSuperUserFeature](./Enable-AipServiceSuperUserFeature.md)

[Configuring super users for Azure Information Protection and discovery services or data recovery](/information-protection/deploy-use/configure-super-users)