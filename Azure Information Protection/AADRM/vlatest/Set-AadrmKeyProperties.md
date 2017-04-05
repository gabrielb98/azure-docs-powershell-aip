---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400592
schema: 2.0.0
ms.assetid: A1C99424-D986-4A5A-B2E1-6D18EEF11B21
---

# Set-AadrmKeyProperties

## SYNOPSIS
Sets the properties of the tenant key. Can activate the key.

## SYNTAX

```
Set-AadrmKeyProperties [-Force] -Active <Bool> -KeyIdentifier <string> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-AadrmKeyProperties** cmdlet sets properties of the tenant key over the Internet to the Azure Rights Management service, can make that key the active tenant key for your tenant. The previously active tenant key is archived.

You must use PowerShell to configure your tenant key; you cannot do this configuration by using a management portal.

Active means that Rights Management uses the key to protect all new content. After set is successful, the previously active key becomes archived.

**Note**: Key state cannot be changed to Archived. To archive specified key you need to select another key to activate.

Warning: Do not run this cmdlet unless you have read and understood the requirements, restrictions, instructions, and implications of migrating from AD RMS to Azure Rights Management. For more information, see [Migrating from AD RMS to Azure RMS](https://docs.microsoft.com/rights-management/plan-design/migrate-from-ad-rms-to-azure-rms) (https://docs.microsoft.com/rights-management/plan-design/migrate-from-ad-rms-to-azure-rms) on the Microsoft documentation site.

If the key is active, users in your organization begin to use the new Azure RMS tenant key to protect documents. Existing users do not start to use the new keys until they are reactivated.

For more information, see [Planning and implementing your Azure Rights Management tenant key](https://docs.microsoft.com/rights-management/plan-design/plan-implement-tenant-key) (https://docs.microsoft.com/rights-management/plan-design/plan-implement-tenant-key) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Activate a tenant key
```
PS C:\> Set-AadrmKeyProperties -Force -KeyIdentifier "c0f102b3-02cc-4816-b732-fcee73edd0e6" -Active $True
```

This command activates the tenant key specified by the *KeyIdentifier* parameter.
Because the command specifies the *Force* parameter, the command does not prompt you for confirmation.

## PARAMETERS

### -Force
Indicates that the cmdlet adds the tenant key silently without prompting you for confirmation.

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

### -KeyIdentifier
Specifies a tenant key indetifier of the key we need to update.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Active
Specifies key state of the key.

Active means that Rights Management uses the key to protect all new content. After set is successful, the previously active key becomes archived.
Specify a value of $True to set the TPD to be active. Users in your organization begin to use the new TPD to help protect documents. Existing users do not start to use the new keys until they are reactivated.

Can only be set to true. Key state cannot be changed to Archived. To archive specified key you need to select another key to activate.

```yaml
Type: Bool
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

[Use-AadrmKeyVaultKey](./Use-AadrmKeyVaultKey.md)

[Get-AadrmKeys](./Get-AadrmKeys.md)
