---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400620
schema: 2.0.0
ms.assetid: C019DD8B-8C2C-487C-B730-38E50A170180
---

# Remove-AadrmRoleBasedAdministrator

## SYNOPSIS
Removes administrative rights from Rights Management.

## SYNTAX

### ObjectId
```
Remove-AadrmRoleBasedAdministrator [-ObjectId <Guid>] [-Role <Role>] [<CommonParameters>]
```

### DisplayName
```
Remove-AadrmRoleBasedAdministrator [-SecurityGroupDisplayName <String>] [-Role <Role>] [<CommonParameters>]
```

### EmailAddress
```
Remove-AadrmRoleBasedAdministrator [-EmailAddress <String>] [-Role <Role>] [<CommonParameters>]
```

## DESCRIPTION
The **Remove-AadrmRoleBasedAdministrator** cmdlet removes administrative rights for a user or group from Azure Rights Management for your organization.

You must use PowerShell to configure delegated administrative control for the Azure Rights Management service; you cannot do this configuration by using a management portal.

Note: One of the parameters for this cmdlet uses the ObjectId (GUID). Because the Office 365 admin center and the Azure Management Portal does not display the GUIDs that are used to identify specific user or groups objects, use the following two steps to find the values that you need to specify the GUIDs.:

1. If you have not already done so, download and install the Azure AD Windows PowerShell module, connect to the service by running [Connect-MsolService](./Connect-MsolService.md), and then run the [Get-MsolGroup](./Get-MsolGroup.md) cmdlet to lookup the GUID of the security group you created to administer role-based administrative rights for Rights Management.

To install the Azure AD module, see "Install the Windows Azure AD Module" section from "Manage Azure AD using Windows PowerShell" (http://msdn.microsoft.com/library/windowsazure/jj151815.aspx).

Tip: If you have many groups, use the **Where-Object** cmdlet in Windows PowerShell to filter results. For example, you might enter the following cmdlet to filter and return only groups that start with "Rights": **Get-MsolGroup | where {$_.DisplayName -like "Rights*" }**

2. In the output of the **Get-MsolGroup** cmdlet, copy the GUID value that was returned and use (paste) that value into the value of the *ObjectId* parameter when you run the **Add-RoleBased Administrator** or [Remove-AadrmRoleBasedAdministrator](./Remove-AadrmRoleBasedAdministrator) cmdlet.

## EXAMPLES

### Example 1: Remove administrative rights by using a display name
```
PS C:\>Remove-AadrmRoleBasedAdministrator -SecurityGroupDisplayName "Finance Employees"
```

This command removes administrative rights from the group named Finance Employees for Rights Management service.

### Example 2: Remove administrative rights by using an email address
```
PS C:\>Remove-AadrmRoleBasedAdministrator -EmailAddress "EvanNarvaez@Contoso.com"
```

This command removes administrative rights from the group that has the specified email address for Rights Management.

## PARAMETERS

### -EmailAddress
Specifies the email address of a user or group.

The cmdlet removes administrative rights for the user or group identified by the email address that you specify.

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
Specifies the GUID of a user or group.

The cmdlet removes administrative rights for the user or group identified by GUID that you specify.

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
Specifies a role. The cmdlet removes an administrator that belongs to the role that you specify.

The acceptable values for this parameter are:

- ConnectorAdministrator
- GlobalAdministrator

If you do not specify a role, the cmdlet removes the administrator from the GlobalAdministrator role.

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
Specifies the display name of a user or group.
The cmdlet removes administrative rights for the user or group identified by the name that you specify.

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

[Add-AadrmRoleBasedAdministrator](./Add-AadrmRoleBasedAdministrator.md)

[Get-AadrmRoleBasedAdministrator](./Get-AadrmRoleBasedAdministrator.md)
