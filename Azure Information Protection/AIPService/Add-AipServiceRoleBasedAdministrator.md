---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 9802F554-834A-4BA0-A086-C7F8B2976939
online version: https://go.microsoft.com/fwlink/?linkid=2044795
schema: 2.0.0
---

# Add-AipServiceRoleBasedAdministrator

## SYNOPSIS
Grants administrative rights to Azure Information Protection.

## SYNTAX

### ObjectId
```
Add-AipServiceRoleBasedAdministrator [-ObjectId <Guid>] [-Role <Role>] [<CommonParameters>]
```

### DisplayName
```
Add-AipServiceRoleBasedAdministrator [-SecurityGroupDisplayName <String>] [-Role <Role>] [<CommonParameters>]
```

### EmailAddress
```
Add-AipServiceRoleBasedAdministrator [-EmailAddress <String>] [-Role <Role>] [<CommonParameters>]
```

## DESCRIPTION
The **Add-AipServiceRoleBasedAdministrator** cmdlet grants administrative rights to the protection service from Azure Information Protection, so that administrators you delegate to configure this service can do so by using PowerShell commands. 

You must use PowerShell to configure delegated administrative control for the protection service; you cannot do this configuration by using a management portal.

When you run this cmdlet, you can specify a user or a group in Azure AD, and you can run the cmdlet multiple times to add new users and new groups. To see the full list, use [Get-AipServiceRoleBasedAdministrator](./Get-AipServiceRoleBasedAdministrator.md).

If you specify a group, it can be any group in Azure AD and does not need to be mail-enabled. To specify a group that is not mail-enabled, use either the *SecurityGroupDisplayName* parameter, or the *ObjectId* parameter. You can also use these parameters or the EmailAddress parameter for a mail-enabled group.

For more information about the user and group requirements, see [Preparing users and groups for Azure Information Protection](/information-protection/plan-design/prepare). This information includes how to identify the different group types and how to find the values to specify them when you run this cmdlet. 

After delegating control to other administrators, they might find it useful to reference a list of the cmdlets they can run, grouped by administrative task. For this information, see [Administering the protection service by using PowerShell](/information-protection/deploy-use/administer-powershell).

Note that these administrative roles are separate from the Azure Active Directory admin roles or Office 365 admin roles.

## EXAMPLES

### Example 1: Grant administrative rights by using a display name
```
PS C:\>Add-AipServiceRoleBasedAdministrator -SecurityGroupDisplayName "Finance Employees"
```

This command grants administrative rights to the protection service for the group that has a display name of **Finance Employees.**

### Example 2: Grant administrative rights by using a GUID
```
PS C:\>Add-AipServiceRoleBasedAdministrator -ObjectId 2c8afe23-bf58-4289-bea1-05131aeb50ab
```

This command grants administrative rights to the protection service  for the group that has the specified GUID.

## PARAMETERS

### -EmailAddress
Specifies the email address of a user or group to have administrative rights for the protection service. If the user has no email address, specify the user's Universal Principal Name.

```yaml
Type: String
Parameter Sets: EmailAddress
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ObjectId
Specifies the GUID of a user or group to have administrative rights for the protection service.

```yaml
Type: Guid
Parameter Sets: ObjectId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Role
Specifies a role of either **Azure Information Protection service global administrator** (the user can configure all aspects of the protection service by using PowerShell commands) or **Azure Information Protection service connector administrator** (the account is granted least privileges to configure and run the Rights Management (RMS) connector).

To specify these roles, use the following values:  

- **GlobalAdministrator**

- **ConnectorAdministrator**

The default value is **GlobalAdministrator.**

```yaml
Type: Role
Parameter Sets: (All)
Aliases:
Accepted values: GlobalAdministrator, ConnectorAdministrator

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SecurityGroupDisplayName
Specifies the display name of a user or group to have administrative rights for the protection service.

```yaml
Type: String
Parameter Sets: DisplayName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AipServiceRoleBasedAdministrator](./Get-AipServiceRoleBasedAdministrator.md)

[Remove-AipServiceRoleBasedAdministrator](./Remove-AipServiceRoleBasedAdministrator.md)