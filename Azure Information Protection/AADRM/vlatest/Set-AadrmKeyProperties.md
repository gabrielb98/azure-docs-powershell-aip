---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400592
schema: 2.0.0
ms.assetid: A1C99424-D986-4A5A-B2E1-6D18EEF11B21
---

# Set-AadrmKeyProperties

## SYNOPSIS
Edit the properties of a key object in the Azure Rights Management Service.

## SYNTAX

```
Set-AadrmKeyProperties [-Force] -KeyIdentifier <string> -Active <Bool> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-AadrmKeyProperties** cmdlet edits the properties of an Azure Rights Management Service key object that is specified by the KeyIdentifier. 

The Azure Rights Management Service uses the Active key object to protect all new content. This cmdlet can set the specified key object as Active for the tenant, in effect "rolling the key" within the Azure Rights Management Service. The previously active key object is automatically set to an Archived state since there can be only one active key at any point in time.

The operation will also re-sign all templates with the new key pair that has been activated. Depending on the number of templates defined, this can be a time-consuming operation, and it is not recommended to run this operation frequently. Existing users will start to use the new key pair when the client machine is bootstrapped again, typically within 30 days.

**Note**: The key object's state cannot be changed to Archived. To archive a specified key object, you need to pick another key object to activate.

Warning: Do not run this cmdlet unless you have read and understood the requirements, restrictions, instructions, and implications of migrating from AD RMS to Azure Rights Management. For more information, see [Migrating from AD RMS to Azure RMS](https://docs.microsoft.com/rights-management/plan-design/migrate-from-ad-rms-to-azure-rms) (https://docs.microsoft.com/rights-management/plan-design/migrate-from-ad-rms-to-azure-rms) on the Microsoft documentation site.

For more information, see [Planning and implementing your Azure Rights Management tenant key](https://docs.microsoft.com/rights-management/plan-design/plan-implement-tenant-key) (https://docs.microsoft.com/rights-management/plan-design/plan-implement-tenant-key) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Activate a different tenant key
```
PS C:\> Set-AadrmKeyProperties -Force -KeyIdentifier "c0f102b3-02cc-4816-b732-fcee73edd0e6" -Active $True
```

This command activates the tenant key specified by the *KeyIdentifier* parameter. The *KeyIdentifier* to be used can be chosen from the output of [Get-AadrmKeys](./Get-AadrmKeys.md).
Because the command specifies the *Force* parameter, the command does not prompt you for confirmation.

## PARAMETERS

### -Force
Indicates that the cmdlet should update the key object silently without prompting for confirmation.

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
Specifies the key identifier for which the properties need to be updated.

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
Changes the state of the key object.

If the state of a key object is *Active*, then the Azure Rights Management Service uses this key to encrypt/decrypt all new content. The parameter only takes a value of $True, and the state of an Active key object cannot be explicitly set to *Archived*. To archive the current active key object, select another key object to activate instead.

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
