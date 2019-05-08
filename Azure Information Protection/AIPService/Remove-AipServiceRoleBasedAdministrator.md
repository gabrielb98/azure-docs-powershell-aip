---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: C019DD8B-8C2C-487C-B730-38E50A170180
online version: https://go.microsoft.com/fwlink/?linkid=2045318
schema: 2.0.0
---

# Remove-AipServiceRoleBasedAdministrator

## SYNOPSIS
Removes administrative rights from Azure Information Protection.

## SYNTAX

### ObjectId
```
Remove-AipServiceRoleBasedAdministrator [-ObjectId <Guid>] [-Role <Role>] [<CommonParameters>]
```

### DisplayName
```
Remove-AipServiceRoleBasedAdministrator [-SecurityGroupDisplayName <String>] [-Role <Role>]
 [<CommonParameters>]
```

### EmailAddress
```
Remove-AipServiceRoleBasedAdministrator [-EmailAddress <String>] [-Role <Role>] [<CommonParameters>]
```

## DESCRIPTION
The **Remove-AipServiceRoleBasedAdministrator** cmdlet removes administrative rights from Azure Information Protection, so that administrators you have previously delegated to configure the protection service can no longer do so by using PowerShell commands.

You must use PowerShell to configure delegated administrative control for the protection service from Azure Information Protection, you cannot do this configuration by using a management portal.

To see the full list of delegated administrators for the protection service, use [Get-AipServiceRoleBasedAdministrator](./Get-AipServiceRoleBasedAdministrator.md). Run the Remove-AipServiceRoleBasedAdministrator cmdlet for each user or group that you want to remove from the list. 

## EXAMPLES

### Example 1: Remove administrative rights by using a display name
```
PS C:\>Remove-AipServiceRoleBasedAdministrator -SecurityGroupDisplayName "Finance Employees"
```

This command removes administrative rights from Azure Information Protection for the group that has a display name of "Finance Employees".

### Example 2: Remove administrative rights by using an email address
```
PS C:\>Remove-AipServiceRoleBasedAdministrator -EmailAddress "EvanNarvaez@Contoso.com"
```

This command removes administrative rights from Azure Information Protection for the user who has an email address of "EvanNarvaez@Contoso.com".

## PARAMETERS

### -EmailAddress
Specifies the email address of a user or group to remove administrative rights from Azure Information Protection. If the user has no email address, specify the user's Universal Principal Name.

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
Specifies the GUID of a user or group to remove administrative rights from Azure Information Protection.

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
Accepted values: GlobalAdministrator, ConnectorAdministrator

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SecurityGroupDisplayName
Specifies the display name of a user or group that should no longer have administrative rights for Azure Information Protection.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AipServiceRoleBasedAdministrator](./Add-AipServiceRoleBasedAdministrator.md)

[Get-AipServiceRoleBasedAdministrator](./Get-AipServiceRoleBasedAdministrator.md)
