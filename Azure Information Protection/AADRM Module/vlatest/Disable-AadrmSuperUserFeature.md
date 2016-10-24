---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400599
schema: 2.0.0
ms.assetid: E6136B57-7B45-4F74-8069-E23FB5D41E17
---

# Disable-AadrmSuperUserFeature

## SYNOPSIS
Disables the super user feature.

## SYNTAX

```
Disable-AadrmSuperUserFeature [<CommonParameters>]
```

## DESCRIPTION
The **Disable-AadrmSuperUserFeature** cmdlet disables the super user feature.
This action does not automatically remove the previously added users or group from the super user list, and they continue to be displayed when you run the Get-AadrmSuperUser or Get-AadrmSuperUserGroup cmdlets.
Therefore, if you enable the super user feature again, these users are automatically super users again, until you manually remove them.
If there are users in the current super list who must not be a super user if this feature is enabled again, remove them from the super user list before you disable the super user feature.
If these users are individually specified, remove them with the Remove-AadrmSuperUser cmdlet.
If they are a member of a group that you have specified to be a super user group, either remove those users from the specified super user group, or remove the super user group by using the Clear-AadrmSuperUserGroup cmdlet.

For information about the super user feature in Azure Rights Management, see Enable-AadrmSuperUserFeature.

## EXAMPLES

### Example 1: Disable super user feature
```
PS C:\>Disable-AadrmSuperUserFeature
```

This command disables the super user feature for your organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Clear-AadrmSuperUserGroup](./Clear-AadrmSuperUserGroup.md)

[Enable-AadrmSuperUserFeature](./Enable-AadrmSuperUserFeature.md)

[Get-AadrmSuperUserFeature](./Get-AadrmSuperUserFeature.md)

[Get-AadrmSuperUser](./Get-AadrmSuperUser.md)

[Get-AadrmSuperUserGroup](./Get-AadrmSuperUserGroup.md)

[Remove-AadrmSuperUser](./Remove-AadrmSuperUser.md)


