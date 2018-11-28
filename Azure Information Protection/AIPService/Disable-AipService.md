---
external help file: AIPService.dll-Help.xml
online version: https://go.microsoft.com/fwlink/?linkid=2044839
schema: 2.0.0
ms.assetid: B0B5958B-F190-469F-8528-EDB9926792CF
---

# Disable-AipService

## SYNOPSIS
Deactivates the protection service from Azure Information Protection.

## SYNTAX

```
Disable-AipService [<CommonParameters>]
```

## DESCRIPTION
The **Disable-AipService** cmdlet deactivates the protection service from Azure Information Protection for your tenant.

You can also do this action in a management portal. For more information, see [Decommissioning and deactivating Azure Information Protection service](https://docs.microsoft.com/rights-management/deploy-use/decommission-deactivate) on the Microsoft documentation site. 

Deactivate the protection service only if you no longer want to protect documents and emails by using Azure Information Protection and you no longer need access to content that was previously protected by using Azure Information Protection.

If you accidentally deactivate the protection service or change your mind, you can simply activate it again by using the [Enable-AipService](./Enable-AipService.md) cmdlet to resume using the service. However, if you are deactivating the service because you no longer want to use protection from Azure Information Protection, you might need to take additional steps. For more information, see [Decommissioning and deactivating Azure Rights Management](https://docs.microsoft.com/rights-management/deploy-use/decommission-deactivate).

## EXAMPLES

### Example 1: Disable the protection service
```
PS C:\>Disable-AipService
```

This command deactivates the protection service from Azure Information Protection.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-AipService](./Enable-AipService.md)

[Get-AipService](./Get-AipService.md)

