---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400596
schema: 2.0.0
ms.assetid: B0B5958B-F190-469F-8528-EDB9926792CF
---

# Disable-AipService

## SYNOPSIS
Deactivates Information Protection service.

## SYNTAX

```
Disable-AipService [<CommonParameters>]
```

## DESCRIPTION
The **Disable-AipService** cmdlet disables the capabilities of Azure Information Protection service for your organization.

You can also do this action in a management portal. For more information, see [Decommissioning and deactivating Azure Information Protection service](https://docs.microsoft.com/rights-management/deploy-use/decommission-deactivate) on the Microsoft documentation site. 

Deactivate Information Protection service only if you no longer want to protect documents and emails by using Azure Information Protection service  and you no longer need access to content that was previously protected by using Information Protection service.

If you accidentally deactivate Azure Information Protection service or change your mind, you can simply activate it again by using the [Enable-AipService](./Enable-AipService.md) cmdlet to resume using the service. However, if you are deactivating Azure Information Protection service because you no longer want to use the service, you might need to take additional steps. For more information, see [Decommissioning and deactivating Azure Information Protection service](https://docs.microsoft.com/rights-management/deploy-use/decommission-deactivate).

## EXAMPLES

### Example 1: Disable Information Protection service
```
PS C:\>Disable-AipService
```

This command deactivates Information Protection service for your organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-AipService](./Enable-AipService.md)

[Get-AipService](./Get-AipService.md)

[Azure Information Protection service](https://docs.microsoft.com/rights-management/deploy-use/decommission-deactivate)
