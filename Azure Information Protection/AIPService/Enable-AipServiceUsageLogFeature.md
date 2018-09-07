---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400605
schema: 2.0.0
ms.assetid: A4ADD1F5-5C7B-482D-8DC2-A2D94A381CF1
---

# Enable-AipServiceUsageLogFeature

## SYNOPSIS
Enables usage logging for Information Protection service.

## SYNTAX

```
Enable-AipServiceUsageLogFeature [<CommonParameters>]
```

## DESCRIPTION
The **Enable-AipServiceUsageLogFeature** cmdlet enables usage logging for Azure Information Protection service. After you enable this feature, Information Protection service logs all requests served on behalf of your tenant to your storage account.

You must use PowerShell to set this configuration; you cannot do this configuration by using a management portal.

Note: This cmdlet is not needed and will not run successfully after the usage logging change in February 2016. After this date, usage logging is automatically enabled and the only Windows PowerShell cmdlet that you need for AIP Service usage logging is [Get-AipServiceUserLog](./Get-AipServiceUserLog.md).

For more information about usage logging, see [Logging and analyzing Azure Information Protection service usage](https://docs.microsoft.com/rights-management/deploy-use/log-analyze-usage) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Enable usage logging
```
PS C:\>Enable-AipServiceUsageLogFeature
Usage logging is enabled for the Information Protection service.
```

This command enables usage logging.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceUsageLogFeature](./Disable-AipServiceUsageLogFeature.md)

[Get-AipServiceUsageLogFeature](./Get-AipServiceUsageLogFeature.md)

[Get-AipServiceUsageLog](./Get-AipServiceUsageLog.md)
