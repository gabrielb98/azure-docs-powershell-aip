---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?LinkId=846352
schema: 2.0.0
ms.assetid: 7b1adf8c-d7a6-42f6-9010-4cc45308691c
---

# Set-AadrmKeyProperties

## SYNOPSIS
Updates the properties of a tenant key object for Rights Management.

## SYNTAX

```
Set-AadrmKeyProperties [-Force] -KeyIdentifier <string> -Active <Bool> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Set-AadrmKeyProperties** cmdlet changes an Archived status for a specified key object for the tenant to be Active. Because there can be only one active tenant key at any one time, the previously active tenant key is automatically set to Archived.

New users of the Azure Rights Management service immediately use the identified tenant key to protect content. Existing users of the service gradually transition from the previously active tenant key to the newly active tenant key, and this staggered transition can take a few weeks to complete. You can force the update on clients by re-initializing the user environment (also known as bootstrapping). Documents and files that were protected with the previously active tenant key remain accessible to authorized users by using the tenant key that is now archived.

Setting the tenant key object status to Active also re-signs all templates with the newly active tenant key. Because this can be a time-consuming operation, especially if you have many templates, we do not recommend that you run this operation frequently. 

To run this cmdlet, you must specify the KeyIdentifier for the tenant key object that you want to set to Active. To get this value, use the [Get-AadrmKeys](./Get-AadrmKeys.md) cmdlet. 

Note that you cannot use this cmdlet to change an Active status to be Archived. To set a tenant key object to have a status of Archived, you must set another tenant key object to Active.

For more information about the tenant key, see [Planning and implementing your Azure Information Protection  tenant key](https://docs.microsoft.com/information-protection/plan-design/plan-implement-tenant-key).

## EXAMPLES

### Example 1: Change the status of a tenant key object to be active
```
PS C:\> Set-AadrmKeyProperties -Force -KeyIdentifier "c0f102b3-02cc-4816-b732-fcee73edd0e6" -Active $True
```

This command changes the status of a tenant key object from Archived to Active. The *KeyIdentifier* parameter identifies the tenant key object to change, and this value can be found by running [Get-AadrmKeys](./Get-AadrmKeys.md). The tenant key object that previously had a status of Active is automatically set to Archived.

Because the command specifies the *Force* parameter, the command does not prompt you for confirmation.

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
Specifies the key identifier for the tenant key object. You can get this value by running [Get-AadrmKeys](./Get-AadrmKeys.md).

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
Sets the status of the tenant key object.

This parameter can only be use with the value of $True, which sets the status to be Active. If you want to change the status of a tenant key object to Archived, you must set another tenant key object to Active.

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

[Get-AadrmKeys](./Get-AadrmKeys.md)
