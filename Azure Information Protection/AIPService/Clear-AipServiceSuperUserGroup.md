---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: F4A1DD4B-C8B9-4FA8-A809-388F01C0A0F0
online version: https://go.microsoft.com/fwlink/?linkid=2045013
schema: 2.0.0
---

# Clear-AipServiceSuperUserGroup

## SYNOPSIS
Removes the super user group for Azure Information Protection.

## SYNTAX

```
Clear-AipServiceSuperUserGroup [<CommonParameters>]
```

## DESCRIPTION
The **Clear-AipServiceSuperUserGroup** cmdlet removes the super user group for Azure Information Protection.

This cmdlet does not affect users that are individually assigned the super user privilege with the [Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md) cmdlet.

You must use PowerShell to configure super users; you cannot do this configuration by using a management portal.

## EXAMPLES

### Example 1: Remove the super user group
```
PS C:\>Clear-AipServiceSuperUserGroup
```

This command removes the super user group, if one exists, for your tenant.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md)

[Get-AipServiceSuperUserGroup](./Get-AipServiceSuperUserGroup.md)

[Set-AipServiceSuperUserGroup](./Set-AipServiceSuperUserGroup.md)