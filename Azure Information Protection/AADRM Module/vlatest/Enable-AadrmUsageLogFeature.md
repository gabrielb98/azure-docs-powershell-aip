---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400605
schema: 2.0.0
ms.assetid: A4ADD1F5-5C7B-482D-8DC2-A2D94A381CF1
---

# Enable-AadrmUsageLogFeature

## SYNOPSIS
Enables usage logging for Rights Management.

## SYNTAX

```
Enable-AadrmUsageLogFeature [<CommonParameters>]
```

## DESCRIPTION
The **Enable-AadrmUsageLogFeature** cmdlet enables usage logging for Azure Rights Management.
After you enable this feature, Rights Management logs all requests served on behalf of your tenant to your storage account.

Note: This cmdlet is not needed and will not run successfully after the usage logging change in February 2016.
After this date, usage logging is automatically enabled and the only Windows PowerShell cmdlet that you need for Azure RMS usage logging is Get-AadrmUserLog.

For more information about usage logging, see Logging and analyzing Azure Rights Management usagehttps://docs.microsoft.com/rights-management/deploy-use/log-analyze-usage (https://docs.microsoft.com/rights-management/deploy-use/log-analyze-usage) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Enable usage logging
```
PS C:\>Enable-AadrmUsageLogFeature 
Usage logging is enabled for the Rights management service.
```

This command enables usage logging.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AadrmUsageLogFeature](./Disable-AadrmUsageLogFeature.md)

[Get-AadrmUsageLogFeature](./Get-AadrmUsageLogFeature.md)

[Get-AadrmUsageLog](./Get-AadrmUsageLog.md)


