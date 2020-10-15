---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 528FCC5D-F653-4B40-8D82-F036BAB66E5C
online version: https://go.microsoft.com/fwlink/?linkid=2045180
schema: 2.0.0
---

# Get-AipServiceRoleBasedAdministrator

## SYNOPSIS
Gets the role-based administrators for Azure Information Protection.

## SYNTAX

```
Get-AipServiceRoleBasedAdministrator [-Role <Role>] [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceRoleBasedAdministrator** cmdlet gets the role-based administrators for the protection service from Azure Information Protection. You can get the administrators for a specified role.

You must use PowerShell to configure delegated administrative control for the protection service; you cannot do this configuration by using a management portal.

## EXAMPLES

### Example 1: List administrators
```
PS C:\>Get-AipServiceRoleBasedAdministrator
```

This command lists the role-based administrators for Azure Information Protection.

## PARAMETERS

### -Role
Specifies a role. The cmdlet gets the administrators that belong to the role that you specify.

The acceptable values for this parameter are:

- ConnectorAdministrator

- GlobalAdministrator

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Add-AipServiceRoleBasedAdministrator](./Add-AipServiceRoleBasedAdministrator.md)

[Remove-AipServiceRoleBasedAdministrator](./Remove-AipServiceRoleBasedAdministrator.md)