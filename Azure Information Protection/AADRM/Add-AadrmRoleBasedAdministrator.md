---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400593
schema: 2.0.0
ms.assetid: 9802F554-834A-4BA0-A086-C7F8B2976939
---

# Add-AadrmRoleBasedAdministrator

## SYNOPSIS
Grants administrative rights to Rights Management.

## SYNTAX

### ObjectId
```
Add-AadrmRoleBasedAdministrator [-ObjectId <Guid>] [-Role <Role>] [<CommonParameters>]
```

### DisplayName
```
Add-AadrmRoleBasedAdministrator [-SecurityGroupDisplayName <String>] [-Role <Role>] [<CommonParameters>]
```

### EmailAddress
```
Add-AadrmRoleBasedAdministrator [-EmailAddress <String>] [-Role <Role>] [<CommonParameters>]
```

## DESCRIPTION
The **Add-AadrmRoleBasedAdministrator** cmdlet grants administrative rights to your organization's Azure Rights Management service, so that administrators you delegate to configure this service can do so by using PowerShell commands. 

You must use PowerShell to configure delegated administrative control for the Azure Rights Management service; you cannot do this configuration by using a management portal.

When you run this cmdlet, you can specify a user or a group in Azure AD, and you can run the cmdlet multiple times to add new users and new groups. To see the full list, use [Get-AadrmRoleBasedAdministrator](./Get-AadrmRoleBasedAdministrator.md).

If you specify a group, it can be any group in Azure AD and does not need to be mail-enabled. To specify a group that is not mail-enabled, use either the *SecurityGroupDisplayName* parameter, or the *ObjectId* parameter. You can also use these parameters or the EmailAddress parameter for a mail-enabled group.

For more information about the user and group requirements, see [Preparing users and groups for Azure Information Protection](https://docs.microsoft.com/information-protection/plan-design/prepare). This information includes how to identify the different group types and how to find the values to specify them when you run this cmdlet. 

After delegating control to other administrators, they might find it useful to reference a list of the cmdlets they can run, grouped by administrative task. For this information, see [Administering the Azure Rights Management service by using Windows PowerShell](/information-protection/deploy-use/administer-powershell).

Note that these administrative roles are separate from the Azure Active Directory admin roles or Office 365 admin roles.

## EXAMPLES

### Example 1: Grant administrative rights by using a display name
```
PS C:\>Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName "Finance Employees"
```

This command grants administrative rights to the Azure Rights Management service for the group that has a display name of "Finance Employees".

### Example 2: Grant administrative rights by using a GUID
```
PS C:\>Add-AadrmRoleBasedAdministrator -ObjectId 2c8afe23-bf58-4289-bea1-05131aeb50ab
```

This command grants administrative rights to the Azure Rights Management service for the group that has the specified GUID.

## PARAMETERS

### -EmailAddress
Specifies the email address of a user or group to have administrative rights for the Azure Rights Management service. If the user has no email address, specify the user's Universal Principal Name.

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
Specifies the GUID of a user or group to have administrative rights for the Azure Rights Management service.

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
Specifies a role of either **Azure Rights Management global administrator** (the user can configure all aspects of the Azure Rights Management service by using PowerShell commands) or **Azure Rights Management connector administrator** (the account is granted least privileges to configure and run the RMS connector).

To specify these roles, use the following values:  

- GlobalAdministrator

- ConnectorAdministrator

The default value is GlobalAdministrator.

```yaml
Type: Role
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SecurityGroupDisplayName
Specifies the display name of a user or group to have administrative rights for the Azure Rights Management service.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AadrmRoleBasedAdministrator](./Get-AadrmRoleBasedAdministrator.md)

[Remove-AadrmRoleBasedAdministrator](./Remove-AadrmRoleBasedAdministrator.md)
