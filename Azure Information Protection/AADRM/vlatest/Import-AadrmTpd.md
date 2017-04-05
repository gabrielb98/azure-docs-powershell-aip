---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?LinkId=521420
schema: 2.0.0
ms.assetid: CA482DE6-8575-4161-AD19-97F8A6C87605
---

# Import-AadrmTpd

## SYNOPSIS
Imports a TPD from AD RMS for Rights Management.

## SYNTAX

```
Import-AadrmTpd [-Force] -TpdFile <String> -ProtectionPassword <SecureString> [-HsmKeyFile <String>]
 [-FriendlyName <String>] [-KeyVaultKeyUrl <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Import-AadrmTpd** cmdlet imports an Active Directory Rights Management Services (AD RMS) trusted publishing domain (TPD) over the Internet into your tenant for Azure Rights Management so that you can migrate Rights Management from on-premises to the cloud.

You must use PowerShell to configure your tenant key; you cannot do this configuration by using a management portal.

This cmdlet sets the TPD to an archived state. The TPD contains your private key and RMS templates.

Warning: Do not run this cmdlet unless you have read and understood the requirements, restrictions, instructions, and implications of migrating from AD RMS to Azure Rights Management. For more information, see [Migrating from AD RMS to Azure RMS](https://docs.microsoft.com/rights-management/plan-design/migrate-from-ad-rms-to-azure-rms) (https://docs.microsoft.com/rights-management/plan-design/migrate-from-ad-rms-to-azure-rms) on the Microsoft documentation site.

After you run this command, the key in the imported TPD becomes available to Azure Rights Management to consume content that AD RMS protected by using this key.

If you migrate templates from your AD RMS as active, you can edit these templates in the Azure classic portal. You can publish these templates so that users can select them from applications. If the migrated templates are not activated, they can only be used to open documents that they previously protected.

You must use the AD RMS management console to export the TPD. If you use a hardware security module (HSM) for your keys, you must first repackage the TPD keys by using the Azure Key Vault BYOK tools. You can download these tools from the [Microsoft Download Site](http://www.microsoft.com/download/details.aspx?id=45345) (http://www.microsoft.com/download/details.aspx?id=45345) For more information, see [How to generate and transfer HSM-protected keys for Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/) (https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/).

## EXAMPLES

### Example 1: Import TPD with a software key
```
PS C:\>$Password = Read-Host -AsSecureString -Prompt "Password: "
PS C:\> Import-AadrmTpd -TpdFile "C:\rms_tpd.xml" -ProtectionPassword $Password -Verbose
```

The first command creates a password as a secure string by using the **Read-Host** cmdlet, and then stores the secure string in the $Password variable. For more information, type `Get-Help Read-Host`.

The second command imports a TPD with a software key.

### Example 2: Import TPD with an HSM key
```
PS C:\>$Password = Read-Host -AsSecureString -Prompt "Password: "
PS C:\> Import-AadrmTpd -TpdFile "C:\no_key_tpd.xml" -ProtectionPassword $Password -KeyVaultKeyUrl "https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333" -FriendlyName "Contoso BYOK key" -Verbose
```

The first command creates a password as a secure string, and then stores the secure string in the $Password variable.

The second command imports a TPD to be used with a key that is stored in Azure Key Vault. Additionaly command changes friendly name of the key to Contoso BYOK key.

Our example uses the key vault name of contoso-byok-kv, the key name of contosorms-byok, and the version number of aaaabbbbcccc111122223333.

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

### -FriendlyName
Specifies the friendly name of the TDP and the key.

This parameter is optional. If friendly name is not supplied, the key name will be used insted.

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

### -HsmKeyFile
Specifies the packaged legacy HSM file that was prepared by using the Azure RMS BYOK tools to upload to your tenant key over the Internet

This parameter is deprecated now that Azure RMS BYOK supports Azure Key Vault, and this parameter is replaced with *KeyVaultKeyUrl*.

If this parameter and the *KeyVaultKeyUrl* parameter are both supplied, this parameter is ignored.

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
Specifies the URL of the key in Azure Key Vault that you want to use for the Azure RMS tenant key. This key will be used in Azure RMS as the root key for all cryptographic operations for your Azure RMS tenant.

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

For example, if your password is **Pa$$word**, enter **'Pa$$word'** or **Pa\`$\`$word** so that Windows PowerShell can correctly parse the special characters.
As a full example, you might type **$pwd = ConvertTo-SecureString 'Pa$$w0rd' -AsPlainText -Force** and then to check that the stored value is correct, type **$pwd** to confirm that **Pa$$word** is displayed.

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
Specifies the TPD file exported from your AD RMS server to import to your Azure Rights Management tenant over the Internet.

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

[Set-AadrmKeyProperties](./Set-AadrmKeyProperties.md)

[Migrating from AD RMS to Azure RMS](https://docs.microsoft.com/rights-management/plan-design/migrate-from-ad-rms-to-azure-rms)

[How to generate and transfer HSM-protected keys for Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/)
