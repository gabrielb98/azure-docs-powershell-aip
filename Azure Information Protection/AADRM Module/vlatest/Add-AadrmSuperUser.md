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
The **Add-AadrmSuperUser** cmdlet adds an individual super user by email address or service principal ID for your organization.
Before you can add a super user, you must enable the super user feature for Azure Rights Management with the Enable-AadrmSuperUserFeature cmdlet.
In addition, the user that you add must have a proxy address, which requires that the user account is either synchronized from Active Directory Domain Services with the attribute set for the proxy address, or that the user is granted a license for Exchange Online.

When you add a super user, that super user is granted full control over all rights-protected content that is managed by Azure Rights Management for your organization.
Use this cmdlet to specify one or more individuals as super users for your organization.
To specify a group whose members have super user privileges, use the Set-AadrmSuperUserGroup cmdlet instead of this **Add-AadrmSuperUser** cmdlet.

Rights Management grants full owner rights to super users for all use licenses that are issued by the subscriber organization.
Super users can decrypt any rights-protected content file and remove rights-protection for it, even if an expiration date has been set and expired.
Typically, this level of access is required for legal eDiscovery and by auditing teams.

## EXAMPLES

### Example 1: Add a user as a super user
```
PS C:\>Add-AadrmSuperUser -EmailAddress "EvanNarvaez@Contoso.com"
```

This command adds an individual user to your organization's super user list for Rights Management by specifying the user's email address.

### Example 2: Add a service principal as a super user
```
PS C:\>Add-AadrmSuperUser -ServicePrincipalId "3C367900-44D1-4865-9379-9A3227042C25"
```

This command adds a service principal to your organization's super user list by specifying the service principal's AppPrincipalId.

## PARAMETERS

### -EmailAddress
Specifies the email address of a user in your organization to which to grant super user privileges.

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
Specifies the **AppPrincipalId** of the service principal to which to grant super user privileges.
Use the Get-MsolServicePrincipal cmdlet to get an existing service principal, or the New-MsolServicePrincipalCredential cmdlet to create a new service principal.

The service principal ID is converted to a pseudo-email address and added to the super users list for the organization.
For example, `Add-AadrmSuperUser -ServicePrincipalId "3C367900-44D1-4865-9379-9A3227042C25"` adds 3C367900-44D1-4865-9379-9A3227042C25@\<rms tenant ID\>.rms.na.aadrm.com to the super user list.

You can remove the service principal from the super user list by using the Remove-AadrmSuperUser cmdlet and this pseudo-email address.
You can use the Get-AadrmSuperUser cmdlet to verify the email address.

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

[Remove-AadrmSuperUser](./Remove-AadrmSuperUser.md)

[Set-AadrmSuperUserGroup](./Set-AadrmSuperUserGroup.md)


