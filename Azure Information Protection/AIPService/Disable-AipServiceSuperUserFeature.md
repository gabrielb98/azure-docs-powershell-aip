---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: E6136B57-7B45-4F74-8069-E23FB5D41E17
online version: https://go.microsoft.com/fwlink/?LinkId=400599
schema: 2.0.0
---

# Disable-AipServiceSuperUserFeature

## SYNOPSIS
Disables the super user feature for Azure Information Protection.

## SYNTAX

```
Disable-AipServiceSuperUserFeature [<CommonParameters>]
```

## DESCRIPTION
The **Disable-AipServiceSuperUserFeature** cmdlet disables the super user feature for Azure Information Protection. This action does not automatically remove the previously added users or group from the super user list, and they continue to be displayed when you run the [Get-AipServiceSuperUser](./Get-AipServiceSuperUser.md) or [Get-AipServiceSuperUserGroup](./Get-AipServiceSuperUserGroup.md) cmdlets. Therefore, if you enable the super user feature again, these users are automatically super users again, until you manually remove them.

If there are users in the current super list who must not be a super user if this feature is enabled again, remove them from the super user list before you disable the super user feature. If these users are individually specified, remove them with the [Remove-AipServiceSuperUser](./Remove-AipServiceSuperUser.md) cmdlet. If they are a member of a group that you have specified to be a super user group, either remove those users from the specified super user group, or remove the super user group by using the [Clear-AipServiceSuperUserGroup](./Clear-AipServiceSuperUserGroup.md) cmdlet.

You must use PowerShell to configure super users; you cannot do this configuration by using a management portal.

For information about the super user feature for Azure Information Protection, see [Enable-AipServiceSuperUserFeature](./Enable-AipServiceSuperUserFeature.md).

## EXAMPLES

### Example 1: Disable the super user feature
```
PS C:\>Disable-AipServiceSuperUserFeature
```

This command disables the super user feature for your tenant.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Clear-AipServiceSuperUserGroup](./Clear-AipServiceSuperUserGroup.md)

[Enable-AipServiceSuperUserFeature](./Enable-AipServiceSuperUserFeature.md)

[Get-AipServiceSuperUserFeature](./Get-AipServiceSuperUserFeature.md)

[Get-AipServiceSuperUser](./Get-AipServiceSuperUser.md)

[Get-AipServiceSuperUserGroup](./Get-AipServiceSuperUserGroup.md)

[Remove-AipServiceSuperUser](./Remove-AipServiceSuperUser.md)