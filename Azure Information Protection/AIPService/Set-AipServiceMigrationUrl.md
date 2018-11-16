---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400622
schema: 2.0.0
ms.assetid: ECE82C74-2902-475D-9DCE-6E9F3842024D
---

# Set-AipServiceMigrationUrl

## SYNOPSIS
Sets a migration URL for Information Protection service.

## SYNTAX

```
Set-AipServiceMigrationUrl -Domain <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-AipServiceMigrationUrl** cmdlet sets a migration URL for Azure Information Protection service.

You must use PowerShell to set the migration URL; you cannot do this action by using a management portal.

Setting a migration URL for newly protected content can help you to migrate from Azure Information Protection service to a supported on-premises Information Protection service server. Do not use this cmdlet in isolation but in conjunction with the instructions from [Decommissioning and deactivating protection for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/decommission-deactivate). 

## EXAMPLES

### Example 1: Set a migration URL
```
PS C:\>Set-AipServiceMigrationUrl -Domain "aadrm.online.contoso.com"
```

This command sets a migration URL for Information Protection service.

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
Prompts you for confirmation before running the cmdlet.

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
Shows what would happen if the cmdlet runs. The cmdlet is not run.

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

[Get-AipServiceMigrationUrl](./Get-AipServiceMigrationUrl.md)

[Microsoft-managed: Tenant key lifecycle operations](https://docs.microsoft.com/information-protection/deploy-use/operations-microsoft-managed-tenant-key)
