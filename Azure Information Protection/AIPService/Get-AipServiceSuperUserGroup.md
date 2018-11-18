---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=722837
schema: 2.0.0
ms.assetid: 697EB0B3-9311-4F45-B1B7-489D7ABF911F
---

# Get-AipServiceSuperUserGroup

## SYNOPSIS
Gets the super user group for Azure Information Protection.

## SYNTAX

```
Get-AipServiceSuperUserGroup [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceSuperUserGroup** cmdlet gets the email address of the Azure Information Protection super user group for your organization. This cmdlet does not get users that are individually assigned as super users with the [Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md) cmdlet.

You must use PowerShell to configure super users; you cannot do this configuration by using a management portal.

For more information about super users, see [Configuring super users for Azure Information Protection and discovery services or data recovery](https://docs.microsoft.com/information-protection/deploy-use/configure-super-users).

## EXAMPLES

### Example 1: Get the super user group
```
PS C:\>Get-AipServiceSuperUserGroup
```

This command gets the email address of the super user group for an organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

### System.String
This operation returns the super user group email address as a **String**. If no super user group exists, an empty **String** is returned.

## NOTES

## RELATED LINKS

[Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md)

[Clear-AipServiceSuperUserGroup](./Clear-AipServiceSuperUserGroup.md)

[Set-AipServiceSuperUserGroup](./Set-AipServiceSuperUserGroup.md)

[Configuring super users for Azure Information Protection and discovery services or data recovery](https://docs.microsoft.com/information-protection/deploy-use/configure-super-users)
