---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400615
schema: 2.0.0
ms.assetid: 4897E667-E8EE-47A0-9F43-2FA3A76D9D38
---

# Get-AipServiceSuperUserFeature

## SYNOPSIS
Gets the status of the super user feature for Azure Information Protection.

## SYNTAX

```
Get-AipServiceSuperUserFeature [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceSuperUserFeature** cmdlet gets the status of the super user feature for Azure Information Protection for your organization. The super user feature can be enabled or disabled. By default, it is disabled.

You must use PowerShell to configure super users; you cannot do this configuration by using a management portal.

For more information about super users, see [Configuring super users for Azure Information Protection and discovery services or data recovery](https://docs.microsoft.com/information-protection/deploy-use/configure-super-users) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Get the status of the super user feature
```
PS C:\>Get-AipServiceSuperUserFeature
Enabled
```

This command gets the status (Enabled or Disabled) of the super user feature in your organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceSuperUserFeature](./Disable-AipServiceSuperUserFeature.md)

[Enable-AipServiceSuperUserFeature](./Enable-AipServiceSuperUserFeature.md)

[Azure Information Protection and discovery services or data recovery](https://docs.microsoft.com/information-protection/deploy-use/configure-super-users)
