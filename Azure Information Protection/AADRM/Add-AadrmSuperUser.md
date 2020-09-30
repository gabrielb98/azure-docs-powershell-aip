---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400594
schema: 2.0.0
ms.assetid: 5B7E7380-C8F4-4113-84D9-B9825F9F2240
---

# Add-AadrmSuperUser

## SYNOPSIS
Adds a super user to Rights Management.

## SYNTAX

### EmailAddress
```
Add-AadrmSuperUser -EmailAddress <String> [<CommonParameters>]
```

### SvcPrincipalId
```
Add-AadrmSuperUser -ServicePrincipalId <String> [<CommonParameters>]
```

## DESCRIPTION
[!INCLUDE [AADRM is deprecated](../includes/aadrm-deprecated.md)]

The **Add-AadrmSuperUser** cmdlet adds an individual account to the super user list for your organization. This operation makes the account a Rights Management owner for all content that is protected by your organization. This means that these super users can decrypt this rights-protected content and remove rights-protection from it, even if an expiration date has been set and expired. Typically, this level of access is required for legal eDiscovery and by auditing teams.

However, before a super user can do these operations, the super user feature for Azure Rights Management must be enabled by using the [Enable-AadrmSuperUserFeature](./Enable-AadrmSuperUserFeature.md) cmdlet. By default, the super user feature is not enabled.

Specify the account by email address or service principal ID. To specify a user who does not have an email address, specify their User Principal Name instead. For more information, see [Preparing users and groups for Azure Information Protection](https://docs.microsoft.com/information-protection/plan-design/prepare). 

To specify a group rather than individual users, use the [Set-AadrmSuperUserGroup](./Set-AadrmSuperUserGroup.md) cmdlet instead of this **Add-AadrmSuperUser** cmdlet.

You must use PowerShell to configure super users; you cannot do this configuration by using a management portal.

## EXAMPLES

### Example 1: Add a user as a super user
```
PS C:\>Add-AadrmSuperUser -EmailAddress "EvanNarvaez@Contoso.com"
```

This command adds an individual user to your organization's super user list for the Azure Rights Management service, by specifying the user's email address.

### Example 2: Add a service principal as a super user
```
PS C:\>Add-AadrmSuperUser -ServicePrincipalId "3C367900-44D1-4865-9379-9A3227042C25"
```

This command adds a service principal to your organization's super user list for the Azure Rights Management service, by specifying the service principal's AppPrincipalId.

## PARAMETERS

### -EmailAddress
Specifies the email address of a user in your organization to grant this user super user privileges.

```yaml
Type: String
Parameter Sets: EmailAddress
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ServicePrincipalId
Specifies the **AppPrincipalId** of the service principal in your organization to grant this account super user privileges. Use the **Get-MsolServicePrincipal** cmdlet to get an existing service principal, or the [New-MsolServicePrincipalCredential](https://docs.microsoft.com/en-us/powershell/module/msonline/new-msolserviceprincipalcredential?view=azureadps-1.0) cmdlet to create a new service principal.

The service principal ID is converted to a pseudo-email address and added to the super user list for the organization. For example, `Add-AadrmSuperUser -ServicePrincipalId "3C367900-44D1-4865-9379-9A3227042C25"` adds 3C367900-44D1-4865-9379-9A3227042C25@\<rms tenant ID\>.rms.na.aadrm.com to the super user list.

You can remove the service principal from the super user list by using the [Remove-AadrmSuperUser](./Remove-AadrmSuperUser.md) cmdlet and this pseudo-email address. You can use the [Get-AadrmSuperUser](./Get-AadrmSuperUser.md) cmdlet to verify the email address.

```yaml
Type: String
Parameter Sets: SvcPrincipalId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-AadrmSuperUserFeature](./Enable-AadrmSuperUserFeature.md)

[Get-AadrmSuperUser](./Get-AadrmSuperUser.md)

[New-MsolServicePrincipalCredential](https://docs.microsoft.com/en-us/powershell/module/msonline/new-msolserviceprincipalcredential?view=azureadps-1.0)

[Remove-AadrmSuperUser](./Remove-AadrmSuperUser.md)

[Set-AadrmSuperUserGroup](./Set-AadrmSuperUserGroup.md)
