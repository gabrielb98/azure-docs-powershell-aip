---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400602
schema: 2.0.0
ms.assetid: 60B3F42C-4FEF-435B-AE28-771932FA6251
---

# Enable-AipService

## SYNOPSIS
Activates Information Protection service for your organization.

## SYNTAX

```
Enable-AipService [<CommonParameters>]
```

## DESCRIPTION
The **Enable-AipService** cmdlet enables your organization to use Azure Information Protection service when you have a subscription that includes this service. 

You can also do this action in a management portal. For more information, see [Activating Azure Information Protection service](https://docs.microsoft.com/information-protection/deploy-use/decommission-deactivate). 

The Azure Information Protection service must be activated before you can begin to use information rights management(IRM) features in Office applications and before you can protect documents and emails by using other applications that use Azure Information Protection service.

When you activate the Information Protection service, you turn on this service for all rights-enabled applications and services, but some applications and services and might need further configuration before they can use Azure Information Protection service.

For more information about activating the Information Protection service and a link to information about the service plans that include Azure Information Protection service, see [Activating Azure Information Protection service](https://docs.microsoft.com/information-protection/deploy-use/activate-service).

For more information about other deployment steps that might be needed, see the [deployment roadmap](https://docs.microsoft.com/information-protection/plan-design/deployment-roadmap).

## EXAMPLES

### Example 1: Enable Information Protection service
```
PS C:\>Enable-AipService
```

This command activates Information Protection service for your organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipService](./Disable-AipService.md)

[Get-AipService](./Get-AipService.md)

[Activating Azure Information Protection service](https://docs.microsoft.com/information-protection/deploy-use/activate-service)

