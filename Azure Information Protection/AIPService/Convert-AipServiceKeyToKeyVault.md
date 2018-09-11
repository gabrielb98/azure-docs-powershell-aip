---
external help file: AIPService.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?LinkId=799850
schema: 2.0.0
ms.assetid: 58EEEE8D-9C0E-4879-8F04-3F56589B1238
---

# Convert-AipServiceKeyToKeyVault

## SYNOPSIS
Changes the location of a legacy customer-managed key in Azure Information Protection service with the location of a customer-managed key in Azure Key Vault.

## SYNTAX

```
Convert-AipServiceKeyToKeyVault -KeyVaultKeyUrl <String> -KeyIdentifier <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Convert-AipServiceKeyToKeyVault** cmdlet is only for customers who have previously created a customer-managed key for the Azure Information Protection service and have received an invitation from Microsoft to migrate their Azure Information Protection service tenant key to Azure Key Vault.

Important: Do not run this cmdlet if you have not received this invitation from Microsoft and do not run this cmdlet without assistance from Microsoft.

You must use PowerShell to configure your tenant key; you cannot do this configuration by using a management portal.

AIP Service now uses Azure Key Vault to manage and monitor a customer-managed AIP Service tenant key. To create a customer-managed AIP Service tenant key for the first time, run [Use-AipServiceKeyVaultKey](./Use-AipServiceKeyVaultKey.md) instead of this cmdlet.

For more information about how to manage your AIP Service tenant key, see [Planning and implementing your Azure Information Protection tenant key](https://docs.microsoft.com/information-protection/plan-design/plan-implement-tenant-key).

Before you run this cmdlet, you will need to identify your original customer-managed AIP Service tenant key. To do that, use the [Get-AipServiceKeys](./Get-AipServiceKeys.md) cmdlet. From the output and identified key, you will need the KeyIdentifier value for the *KeyIdentifier* parameter when you run this cmdlet.

Also, your organization's administrator for Azure Key Vault must create a new key for AIP Service and supply you with a URL for this key. You will need to specify the URL for the *KeyVaultKeyUrl* parameter when you run this cmdlet. This Azure Key Vault administrator must also grant AIP Service access to the key vault that contains the key.

For security reasons, this cmdlet does not let you change the access control for the key; this must be done from Key Vault.

## EXAMPLES

### Example 1: Change the location of a legacy AIP Service tenant key with a key in Azure Key Vault
```
PS C:\>Convert-AipServiceKeyToKeyVault -KeyIdentifier aaaaaaaa-1111-2222-3333-bbbbbbbbbbbb -KeyVaultKeyUrl "https://contoso.vault.azure.net/keys/contoso-aipservice-key/aaaabbbbcccc111122223333"
```

Changes the location of the original customer-managed key in AIP Service that has the key identifier of aaaaaaaa-1111-2222-3333-bbbbbbbbbbbb with the location of a customer-managed key in Azure Key Vault, which is named contoso-aipservice-key and has the version number aaaabbbbcccc111122223333 in the Contoso key vault.

## PARAMETERS

### -Force
Forces the command to run without asking for user confirmation.

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
Specifies the key identifier value of the original customer-managed AIP Service tenant key that you now want to manage from Azure Key Vault.

To get the key identifier value, use the **Get-AipServiceKeys** cmdlet.

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

### -KeyVaultKeyUrl
Specifies the URL of the key in Azure Key Vault that you want to use for the AIP Service tenant key. This key will be used in AIP Service as the root key for all cryptographic operations for your AIP Service tenant.

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

[Get-AipServiceKeys](./Get-AipServiceKeys.md)

[Use-AipServiceKeyVaultKey](./Use-AipServiceKeyVaultKey.md)

[Planning and implementing your Azure Information Protection tenant key](https://docs.microsoft.com/information-protection/plan-design/plan-implement-tenant-key)
