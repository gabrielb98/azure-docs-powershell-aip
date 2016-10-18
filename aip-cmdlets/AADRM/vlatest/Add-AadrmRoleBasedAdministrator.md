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
The **Add-AadrmRoleBasedAdministrator** cmdlet grants administrative rights to Azure Rights Management within your organization.
Specify a user or group to have administrative rights.

This cmdlet adds a member user or group to the list of users and groups that can administer Rights Management.
By default, all Microsoft Office 365 global administrators can run all the Windows PowerShell cmdlets for Rights Management.
If you have to grant rights to another administrator within your organization, use this cmdlet to specify a security group that can administer the service.

Note: One of the parameters for this cmdlet uses the ObjectId (GUID).
Because the Office 365 admin center and the Azure classic portal does not display the GUIDs that are used to identify specific user or groups objects, use the following two steps to find the values that you need to specify the GUIDs.:

1.
If you have not already done so, download and install the Azure AD PowerShell module, connect to the service by running **Connect-MsolService**, and then run the **Get-MsolGroup** cmdlet to lookup the GUID of the security group you created to administer role-based administrative rights for Rights Management.
To install the Azure AD module, see the Install the Windows Azure AD Module section from the Manage Azure AD using Windows PowerShell (http://msdn.microsoft.com/library/windowsazure/jj151815.aspx) topic.

Tip: If you have many groups, use the **Where-Object** cmdlet in Windows PowerShell to filter results.
For example, you might enter the following cmdlet to filter and return only groups that start with "Rights": **Get-MsolGroup | where {$_.DisplayName -like "Rights*" }**

2.
In the output of the **Get-MsolGroup** cmdlet, copy the GUID value that was returned and use (paste) that value into the value of the -ObjectId parameter when you run the **Add-RoleBased Administrator** or Remove-AadrmRoleBasedAdministrator cmdlet.

## EXAMPLES

### Example 1: Grant administrative rights by using a display name
```
PS C:\>Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName "Finance Employees"
```

This command grants administrative rights to Rights Management for the group named Finance Employees.

### Example 2: Grant administrative rights by using a GUID
```
PS C:\>Add-AadrmRoleBasedAdministrator -ObjectId 2c8afe23-bf58-4289-bea1-05131aeb50ab
```

This command grants administrative rights to Rights Management for the group that has the specified GUID.

## PARAMETERS

### -EmailAddress
Specifies the email address of a user or group.
The cmdlet adds administrative rights for the user or group that is identified by the email address that you specify.

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
The cmdlet adds administrative rights for the user or group that is identified by a GUID that you specify.

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
Specifies a role of either **Azure Rights Management global administrator** (the user can configure all aspects of Azure RMS by using Azure RMS PowerShell commands) or **Azure Rights Management connector administrator** (the account is granted least privileges to configure and run the RMS connector).
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
Specifies the display name of a user or group.
The cmdlet adds administrative rights for the user or group that is identified by the name that you specify.

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

[Get-AadrmRoleBasedAdministrator](.\Get-AadrmRoleBasedAdministrator.md)

[Remove-AadrmRoleBasedAdministrator](.\Remove-AadrmRoleBasedAdministrator.md)


