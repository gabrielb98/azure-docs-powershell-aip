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
Use-AadrmKeyVaultKey -KeyVaultKeyUrl <String> [-FriendlyName <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Use-AadrmKeyVaultKey** cmdlet tells the Azure Rights Management service to use a customer-managed key (BYOK) that has been created by an administrator in your organization who is responsible for managing Azure Key Vault. This key then becomes the customer-managed tenant key for the Azure Rights Management service in your organization.

You must use PowerShell to configure your tenant key; you cannot do this configuration by using a management portal.

You can run this cmdlet before or after the Azure Rights Management service is activated. In either case, your tenant key in Azure Key Vault will automatically include the initial key that Microsoft generated (a Microsoft-managed key) when the tenant for the Azure Rights Management service was first created.

After you run this cmdlet, the Azure Rights Management service uses Azure Key Vault to centrally manage and monitor use of your tenant key. All calls to your tenant key will be made to and from a key vault that your organization owns. You can confirm which key you are using in Key Vault by using the [Get-AadrmKeys](./Get-AadrmKeys.md) cmdlet.

For more information about the types of tenant keys that the Azure Rights Management service supports, see [Planning and implementing your Azure Information Protection tenant key](/information-protection/plan-design/plan-implement-tenant-key).

For more information about Azure Key Vault, see [What is Azure Key Vault](/azure/key-vault/key-vault-whatis).

For security reasons, this cmdlet does not let you set or change the access control for your tenant key in Key Vault. Instead, this must be done by your organization's administrator for Azure Key Vault. After that access is granted, run this cmdlet to tell the Azure Rights Management service to use the key and version that you specify with the *KeyVaultKeyUrl* parameter.

## EXAMPLES

### Example 1: Configure the Azure Rights Management service to use a customer-managed key in Azure Key Vault
```
PS C:\>Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contoso.vault.azure.net/keys/contoso-rms-key/aaaabbbbcccc111122223333"
```

This command tells the Azure Rights Management service to use the key named contoso-rms-key, version aaaabbbbcccc111122223333, in the key vault named contoso.

This key and version in Azure Key Vault then becomes the customer-managed tenant key for the Azure Rights Management service.

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

This key will be used by the Azure Rights Management service as the root key for all cryptographic operations for your tenant.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AadrmKeys](./Get-AadrmKeys.md)

[Set-AadrmKeyProperties](./Set-AadrmKeyProperties.md)

[Planning and implementing your Azure Rights Management tenant key](/information-protection/plan-design/plan-implement-tenant-key)

[What is Azure Key Vault](/azure/key-vault/key-vault-whatis)
