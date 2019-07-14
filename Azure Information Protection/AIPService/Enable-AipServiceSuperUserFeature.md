---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 34D77711-B96A-43E8-B5FD-8CF5013EB7E3
online version: https://go.microsoft.com/fwlink/?linkid=2044936
schema: 2.0.0
---

# Enable-AipServiceSuperUserFeature

## SYNOPSIS
Enables the super user feature for Azure Information Protection.

## SYNTAX

```
Enable-AipServiceSuperUserFeature [<CommonParameters>]
```

## DESCRIPTION
The **Enable-AipServiceSuperUserFeature** cmdlet enables the super user feature for your tenant's protection service from Azure Information Protection. When this feature is enabled, any users that are defined as super users for your organization (individually or by the super user group) can decrypt content that your tenant protected, and can remove protection from this content, even if an expiration date has been set and expired. Typically, this level of access is required for legal eDiscovery and by auditing teams. 

You must use PowerShell to configure super users; you cannot do this configuration by using a management portal.

By default, the super user feature is not enabled, and no users are assigned to this feature. To assign users, you must use [Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md) or [Set-AipServiceSuperUserGroup](./Set-AipServiceSuperUserGroup.md).

Caution: We recommend that you enable the super user feature on an as-needed basis. During standard operations, we recommend that you disable the super user feature, unless you use it to provide a trusted application with the ability to decrypt rights-protected content. For example, this exception might be needed for an application to scan the contents of a file for malware.

## EXAMPLES

### Example 1: Enable the super user feature
```
PS C:\>Enable-AipServiceSuperUserFeature
```

This command enables the super user feature for your tenant.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceSuperUserFeature](./Disable-AipServiceSuperUserFeature.md)

[Get-AipServiceSuperUserFeature](./Get-AipServiceSuperUserFeature.md)
