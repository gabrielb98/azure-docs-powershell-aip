---
external help file: AIPService.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?LinkId=799849
schema: 2.0.0
ms.assetid: 2EC79F48-DC64-42D0-B317-89397A72243D
---

# Use-AipServiceKeyVaultKey

## SYNOPSIS
Tells Azure Information Protection to use a customer-managed tenant key in Azure Key Vault.

## SYNTAX

```
Use-AipServiceKeyVaultKey -KeyVaultKeyUrl <String> [-FriendlyName <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Use-AipServiceKeyVaultKey** cmdlet tells Azure Information Protection to use a customer-managed key (BYOK) in Azure Key Vault.

You must use PowerShell to configure your tenant key; you cannot do this configuration by using a management portal.

You can run this cmdlet before or after the protection service (Azure Rights Management) is activated. 

Before you run this cmdlet, make sure that the Azure Rights Management service principal has been granted permissions to the key vault that contains the key you want to use for Azure Information Protection. These permissions are granted by running the Azure Key Vault cmdlet, [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy).  

For security reasons, the Use-AipServiceKeyVaultKey cmdlet does not let you set or change the access control for the key in Azure Key Vault. After that access is granted by running Set-AzureRmKeyVaultAccessPolicy, run Use-AipServiceKeyVaultKey to tell Azure Information Protection to use the key and version that you specify with the *KeyVaultKeyUrl* parameter.

Note: If you run this cmdlet before the permissions are granted to the key vault, you will see an error that displays **The Rights Management service failed to add the key**. To see more detailed information, run the command again, with -*Verbose*. If the permissions are not granted, you see **VERBOSE: Failure to access Azure KeyVault**.

When your command successfully runs, the key is added as an archived customer-managed tenant key for Azure Information Protection for your organization. To make it the active tenant key for Azure Information Protection, you must then run the [Set-AipServiceKeyProperties](./Set-AipServiceKeyProperties.md) cmdlet.

Use Azure Key Vault to centrally manage and monitor use of the key that you specified. All calls to your tenant key will be made to the key vault that your organization owns. You can confirm which key you are using in Key Vault by using the [Get-AipServiceKeys](./Get-AipServiceKeys.md) cmdlet.

For more information about the types of tenant keys that Azure Information Protection supports, see [Planning and implementing your Azure Information Protection tenant key](https://docs.microsoft.com/information-protection/plan-design/plan-implement-tenant-key).

For more information about Azure Key Vault, see [What is Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-whatis).


## EXAMPLES

### Example 1: Configure Azure Information Protection to use a customer-managed key in Azure Key Vault
```
PS C:\>Use-AipServiceKeyVaultKey -KeyVaultKeyUrl "https://contoso.vault.azure.net/keys/contoso-aipservice-key/aaaabbbbcccc111122223333"
```

This command tells Azure Information Protection to use the key named contoso-aipservice-key, version aaaabbbbcccc111122223333, in the key vault named contoso.

This key and version in Azure Key Vault then becomes the customer-managed tenant key for Azure Information Protection.

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
Specifies the URL of the key and version in Azure Key Vault that you want to use for your tenant key.

This key will be used by Azure Information Protection as the root key for all cryptographic operations for your tenant.

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

### -FriendlyName
Specifies the friendly name of a trusted publishing domain (TPD) and the SLC key that you imported from AD RMS. If users run Office 2016 or Office 2013, specify the same **Friendly name** value that is set for the AD RMS cluster properties on the **Server Certificate** tab. 

This parameter is optional. If you don't use it, the key identifier is used instead.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AipServiceKeys](./Get-AipServiceKeys.md)

[Set-AipServiceKeyProperties](./Set-AipServiceKeyProperties.md)

