---
external help file: AipService.dll-Help.xml
Module Name: AIPService
ms.assetid: 9B4056B1-7BEB-4DD2-A0C7-2F9400EDB3E5
online version: https://go.microsoft.com/fwlink/?linkid=2044896
schema: 2.0.0
---

# Get-AipServiceKeys

## SYNOPSIS
Lists all Azure Information Protection tenant keys associated with your tenant.

## SYNTAX

```
Get-AipServiceKeys [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceKeys** cmdlet lists all Azure Information Protection tenant keys associated with your tenant. The tenant keys include the initial tenant key that Microsoft generates for you, and any tenant keys that are stored in Azure Key Vault. For more information, see [Planning and implementing your Azure Information Protection tenant key](/information-protection/plan-design/plan-implement-tenant-key).

You must use PowerShell to configure your tenant key; you cannot do this configuration by using a management portal.

For security reasons, the cmdlet does not display the value of the tenant keys.

When you run this cmdlet, you will see **Status** and **KeyType**:

- The **Status** value shows **Archived** or **Active**. Archived identifies a tenant key that can be used to open previously protected content. Active identities the tenant key is currently in use to protect content.

- The **KeyType** value shows **Microsoft-managed** or **Customer-managed (BYOK)**. Microsoft-managed identifies the tenant key as managed by Microsoft (the default). Customer-managed identifies the tenant key as managed by your organization in Azure Key Vault. For a customer-managed key, you also see **Publickey**, which shows the base-64 encoded public key that is associated with the KeyIdentifier and that corresponds to the same information that Azure Key Vault provides for your key.

For security reasons, the cmdlet does not display the value of the Microsoft-managed key and displays only the public key information of customer-managed (BYOK) keys.

## EXAMPLES

### Example 1: Get keys
```
PS C:\>Get-AipServiceKeys
```

This command lists all Azure Information Protection tenant keys associated with your tenant.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Import-AipServiceTpd](./Import-AipServiceTpd.md)

[Planning and implementing your Azure Information Protection tenant key](/information-protection/plan-design/plan-implement-tenant-key)