---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 48A3F450-B87B-43DB-8723-8917FD5E0B7B
online version: https://go.microsoft.com/fwlink/?linkid=2045326
schema: 2.0.0
---

# Remove-AipServiceSuperUser

## SYNOPSIS
Removes a super user from Azure Information Protection.

## SYNTAX

```
Remove-AipServiceSuperUser -EmailAddress <String> [<CommonParameters>]
```

## DESCRIPTION
The **Remove-AipServiceSuperUser** cmdlet removes a user from the list of users who are individually granted super user privileges for your organization.

This cmdlet does not remove a group or a user from that a group that is assigned super user privileges by using the [Set-AipServiceSuperUserGroup](./Set-AipServiceSuperUserGroup.md) cmdlet.

For more information about super users, see the [Get-AipServiceSuperUser](./Get-AipServiceSuperUser.md) cmdlet.

You must use PowerShell to configure super users; you cannot do this configuration by using a management portal.

## EXAMPLES

### Example 1: Remove a super user
```
PS C:\>Remove-AipServiceSuperUser -EmailAddress "EvanNarvaez@Contoso.com"
```

This command removes an individually specified super user from Azure Information Protection by specifying that user's email address.

## PARAMETERS

### -EmailAddress
Specifies the email address of a user or group. 

The cmdlet removes the user or group identified by the email address that you specify.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AipServiceSuperUser](./Add-AipServiceSuperUser.md)

[Get-AipServiceSuperUser](./Get-AipServiceSuperUser.md)

[Enable-AipServiceSuperUserFeature](./Enable-AipServiceSuperUserFeature.md)

[Set-AipServiceSuperUserGroup](./Set-AipServiceSuperUserGroup.md)