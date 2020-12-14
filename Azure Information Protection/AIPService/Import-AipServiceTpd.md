---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: CA482DE6-8575-4161-AD19-97F8A6C87605
online version: https://go.microsoft.com/fwlink/?linkid=2045514
schema: 2.0.0
---

# Import-AipServiceTpd

## SYNOPSIS
Imports a TPD from AD RMS for Azure Information Protection.

## SYNTAX

```
Import-AipServiceTpd [-Force] -TpdFile <String> -ProtectionPassword <SecureString> [-FriendlyName <String>]
 [-KeyVaultKeyUrl <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Import-AipServiceTpd** cmdlet imports an Active Directory Rights Management Services (AD RMS) trusted publishing domain (TPD) over the Internet into your tenant for Azure Information Protection, so that you can migrate your protection service from on-premises to the cloud. The TPD contains your private key and protection templates from AD RMS.

You must use PowerShell to configure your tenant key; you cannot do this configuration by using a management portal.

This cmdlet always sets the key from the imported TPD to an archived state. After you run this command, the key in the imported TPD becomes available to Azure Information Protection to consume content that AD RMS protected by using this key. Use the [Set-AipServiceKeyProperties](./Set-AipServiceKeyProperties.md) cmdlet to change the state of the imported TPD to Active.

> [!WARNING]
> Do not run this cmdlet unless you have read and understood the requirements, restrictions, instructions, and implications of migrating from AD RMS. 
>
> For more information, see [Migrating from AD RMS to Azure Information Protection](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms).
> 
If you migrate templates from AD RMS as active, you can edit these templates in the Azure portal, or by using PowerShell. You can publish these templates so that users can select them from applications. If the migrated templates are not activated, they can only be used to open documents that they previously protected.

You must use the AD RMS management console to export the TPD. If you use a hardware security module (HSM) for your keys, you must first repackage the TPD keys by using the Azure Key Vault BYOK tools. You can download these tools from the [Microsoft Download Site](https://www.microsoft.com/download/details.aspx?id=45345). 

For more information, see [How to generate and transfer HSM-protected keys for Azure Key Vault](/azure/key-vault/key-vault-hsm-protected-keys).

## EXAMPLES

### Example 1: Import TPD with a software key
```
PS C:\>$Password = Read-Host -AsSecureString -Prompt "Password: "
PS C:\> Import-AipServiceTpd -TpdFile "C:\aipservice_tpd.xml" -ProtectionPassword $Password -Verbose
```

The first command creates a password as a secure string by using the **Read-Host** cmdlet, and then stores the secure string in the $Password variable. For more information, type `Get-Help Read-Host`.

The second command imports a TPD with a software key.

### Example 2: Import TPD with an HSM key
```
PS C:\>$Password = Read-Host -AsSecureString -Prompt "Password: "
PS C:\> Import-AipServiceTpd -TpdFile "C:\no_key_tpd.xml" -ProtectionPassword $Password -KeyVaultKeyUrl "https://contoso-byok-kv.vault.azure.net/keys/contosoaipservice-byok/aaaabbbbcccc111122223333" -FriendlyName "Contoso BYOK key" -Verbose
```

The first command creates a password as a secure string, and then stores the secure string in the **$Password** variable.

The second command imports a TPD to be used with a key that is stored in Azure Key Vault. Additionally, the command changes the friendly name of the key to **"Contoso BYOK key"**.

Our example uses the key vault name of **contoso-byok-kv**, the key name of **contosoaipservice-byok**, and the version number of **aaaabbbbcccc111122223333**.

## PARAMETERS

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

### -KeyVaultKeyUrl
Specifies the URL of the key in Azure Key Vault that you want to use for your tenant key. This key will be used by Azure Information Protection as the root key for all cryptographic operations for your tenant.

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

### -ProtectionPassword
Specifies the password that was used to encrypt the exported TPD file.

You can use either **ConvertTo-SecureString -AsPlaintext** or **Read-Host** to specify the SecureString.

When you use **ConvertTo-SecureString** and the password has special characters, enter the password between single quotes or escape the special characters. If you do not, the password will not parse correctly and in verbose mode, you will see the following error messages:

**VERBOSE: Trusted Publishing Domain data is corrupted.**
**VERBOSE: The remote server returned an unexpected response: (400) Bad Request.**

For example, if your password is **Pa$$word**, enter **'Pa$$word'** or **Pa\`$\`$word** so that Windows PowerShell can correctly parse the special characters. As a full example, you might type **$pwd = ConvertTo-SecureString 'Pa$$w0rd' -AsPlainText -Force** and then to check that the stored value is correct, type **$pwd** to confirm that **Pa$$word** is displayed.

```yaml
Type: SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TpdFile
Specifies the TPD file exported from your AD RMS cluster to import to your tenant to use for Azure Information Protection.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. 

For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Set-AipServiceKeyProperties](./Set-AipServiceKeyProperties.md)

[Migrating from AD RMS to Azure Information Protection](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

[How to generate and transfer HSM-protected keys for Azure Key Vault](/azure/key-vault/key-vault-hsm-protected-keys)