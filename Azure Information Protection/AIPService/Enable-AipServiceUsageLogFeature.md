---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400605
schema: 2.0.0
ms.assetid: A4ADD1F5-5C7B-482D-8DC2-A2D94A381CF1
---

# Enable-AipServiceUsageLogFeature

## SYNOPSIS
Enables protection usage logging for Azure Information Protection.

## SYNTAX

```
Enable-AipServiceUsageLogFeature [<CommonParameters>]
```

## DESCRIPTION
The **Enable-AipServiceUsageLogFeature** cmdlet enables protection usage logging for Azure Information Protection. After you enable this feature, Azure Information Protection logs all protection requests served on behalf of your tenant to your storage account.

You must use PowerShell to set this configuration; you cannot do this configuration by using a management portal.

Note: This cmdlet is not needed and will not run successfully after the protection usage logging change in February 2016. After this date, usage logging for the protection service is automatically enabled and the only PowerShell cmdlet that you need is [Get-AipServiceUserLog](./Get-AipServiceUserLog.md).

For more information about usage logging for the protection service, see [Logging and analyzing the protection usage from Azure Information Protection](https://docs.microsoft.com/rights-management/deploy-use/log-analyze-usage) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Enable usage logging
```
PS C:\>Enable-AipServiceUsageLogFeature
Usage logging is enabled for Azure Information Protection.
```

This command enables usage logging for the protection service.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AipServiceUsageLogFeature](./Disable-AipServiceUsageLogFeature.md)

[Get-AipServiceUsageLogFeature](./Get-AipServiceUsageLogFeature.md)

[Get-AipServiceUsageLog](./Get-AipServiceUsageLog.md)
