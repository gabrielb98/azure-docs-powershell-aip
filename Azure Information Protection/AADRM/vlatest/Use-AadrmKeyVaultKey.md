---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?LinkId=799849
schema: 2.0.0
ms.assetid: 2EC79F48-DC64-42D0-B317-89397A72243D
---

# Use-AadrmKeyVaultKey

## SYNOPSIS
Tells Rights Management to use a customer-managed tenant key in Azure Key Vault.

## SYNTAX

```
Use-AadrmKeyVaultKey -KeyVaultKeyUrl <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Use-AadrmKeyVaultKey** cmdlet tells Azure RMS to use a customer-managed key (BYOK) that has been created by an administrator in your organization who is responsible for managing Azure Key Vault.
This key then becomes the customer-managed tenant key for Azure RMS in your organization.

You can run this cmdlet before or after Azure RMS is activated.
In either case, your Azure RMS tenant key in Azure Key Vault will automatically include the initial key that Microsoft generated (a Microsoft-managed key) when the Azure RMS tenant was first created.

After you run this cmdlet, Azure RMS uses Azure Key Vault to centrally manage and monitor use of your Azure RMS tenant key.
All calls to your Azure RMS tenant key will be made to and from a key vault that your organization owns.
You can confirm which key you are using in Key Vault by using the [Get-AadrmKeys](./Get-AadrmKeys.md) cmdlet.

For more information about the types of tenant keys that Azure RMS supports, see [Planning and implementing your Azure Rights Management tenant key](https://docs.microsoft.com/en-us/rights-management/plan-design/plan-implement-tenant-key) (https://docs.microsoft.com/rights-management/plan-design/plan-implement-tenant-key).
For more information about Azure Key Vault, see [What is Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-whatis) (https://azure.microsoft.com/documentation/articles/key-vault-whatis/).

For security reasons, this cmdlet does not let you set or change the access control for your Azure RMS tenant key in Key Vault.
Instead, this must be done by your organization's administrator for Azure Key Vault.
After that access is granted, run this cmdlet to tell Azure RMS to use the key and version that you specify with the *KeyVaultKeyUrl* parameter.

## EXAMPLES

### Example 1: Configure Azure RMS to use a customer-managed key in Azure Key Vault
```
PS C:\>Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contoso.vault.azure.net/keys/contoso-rms-key/aaaabbbbcccc111122223333"
```

This command tells Azure RMS to use the key named contoso-rms-key, version aaaabbbbcccc111122223333, in the key vault named contoso.
This key and version in Azure Key Vault then becomes the customer-managed tenant key for Azure RMS.

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

### -KeyVaultKeyUrl
Specifies the URL of the key and version in Azure Key Vault that you want to use for the Azure RMS tenant key.
This key will be used in Azure RMS as the root key for all cryptographic operations for your Azure RMS tenant.

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
Shows what would happen if the cmdlet runs.
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

[Get-AadrmKeys](./Get-AadrmKeys.md)

[Planning and implementing your Azure Rights Management tenant key](https://docs.microsoft.com/en-us/rights-management/plan-design/plan-implement-tenant-key)

[What is Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-whatis)
