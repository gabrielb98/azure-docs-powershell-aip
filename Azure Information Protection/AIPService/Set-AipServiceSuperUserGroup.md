---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 23E946A0-E6FC-4F8C-8F3B-352AD48CE426
online version: https://go.microsoft.com/fwlink/?linkid=2045240
schema: 2.0.0
---

# Set-AipServiceSuperUserGroup

## SYNOPSIS
Sets the super user group for Azure Information Protection.

## SYNTAX

```
Set-AipServiceSuperUserGroup -GroupEmailAddress <String> [<CommonParameters>]
```

## DESCRIPTION
The **Set-AipServiceSuperUserGroup** cmdlet specifies a group to use as the super user group for Azure Information Protection. Members of this group are then super users, which means they become an owner for all content that is protected by your organization. These super users can decrypt this protected content and remove protection from it, even if an expiration date has been set and expired. Typically, this level of access is required for legal eDiscovery and by auditing teams.

You can specify any group that has an email address, but be aware that for performance reasons, group membership is cached. For information about group requirements, see [Preparing users and groups for Azure Information Protection](https://docs.microsoft.com/information-protection/plan-design/prepare).

If a super user group already exists, running this cmdlet overwrites it. This cmdlet does not affect users that are individually assigned as super users with the [Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md) cmdlet.

An organization can have only one super user group in addition to multiple users who are assigned the privilege individually, but you can nest groups.

You must use PowerShell to configure super users; you cannot do this configuration by using a management portal.

For more information about super users, see [Configuring super users for Azure Information Protection and discovery services or data recovery](https://docs.microsoft.com/information-protection/deploy-use/configure-super-users).

## EXAMPLES

### Example 1: Set the super user group
```
PS C:\>Set-AipServiceSuperUserGroup -GroupEmailAddress "SuperUserGroup@contoso.com"
```

This command sets the super user group for the organization to SuperUserGroup@contoso.com.

## PARAMETERS

### -GroupEmailAddress
Specifies the group email address for the super user group.

*GroupEmailAddress* can specify a group that contains individual users or other nested groups. It must be a valid group email address for an existing group in the organization.


```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md)

[Clear-AipServiceSuperUserGroup](./Clear-AipServiceSuperUserGroup.md)

[Get-AipServiceSuperUserGroup](./Get-AipServiceSuperUserGroup.md)
