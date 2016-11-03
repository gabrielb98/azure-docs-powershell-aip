---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400622
schema: 2.0.0
ms.assetid: ECE82C74-2902-475D-9DCE-6E9F3842024D
---

# Set-AadrmMigrationUrl

## SYNOPSIS
Sets the migration URL for Rights Management.

## SYNTAX

```
Set-AadrmMigrationUrl -Domain <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-AadrmMigrationUrl** cmdlet sets the migration URL for Azure Rights Management.

Migration URLs let you migrate from Rights Management to a supported on-premises Rights Management server.
Use this migration technique if you need indefinite access to content that has been previously protected by using Azure Rights Management and you have decided to no longer use Azure Rights Management.

In addition to setting this migration URL for clients, you must export your keys and policies from the cloud service in the form of a trusted publishing domain (TPD file) and import them into an on-premises Rights Management server.
For more information, see the instructions for exporting your tenant key in Microsoft-managed: Tenant key lifecycle operationshttps://docs.microsoft.com/rights-management/deploy-use/operations-microsoft-managed-tenant-key (https://docs.microsoft.com/rights-management/deploy-use/operations-microsoft-managed-tenant-key) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Set a migration URL
```
PS C:\>Set-AadrmMigrationUrl -Domain "aadrm.online.contoso.com"
```

This command sets a migration URL for Rights Management.

## PARAMETERS

### -Domain
Specifies a URL for the domain to migrate.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Indicates that the cmdlet sets the value of the migration URL even if there is an existing migration URL.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AadrmMigrationUrl](./Get-AadrmMigrationUrl.md)


