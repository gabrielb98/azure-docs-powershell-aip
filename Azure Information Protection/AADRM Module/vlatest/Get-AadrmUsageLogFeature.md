---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400617
schema: 2.0.0
ms.assetid: C63B5A33-75B8-43A4-83E2-F6AF477A5BBF
---

# Get-AadrmUsageLogFeature

## SYNOPSIS
Gets the status of usage logging for Rights Management.

## SYNTAX

```
Get-AadrmUsageLogFeature [<CommonParameters>]
```

## DESCRIPTION
The **Get-AadrmUsageLogFeature** cmdlet gets the status of usage logging for Azure Rights Management.

Note: This cmdlet always returns **False** after the usage logging change in February 2016.
After this date, usage logging is enabled automatically and the only Windows PowerShell cmdlet that you need for Azure RMS usage logging is Get-AadrmUserLog.

For more information about usage logging, see Logging and analyzing Azure Rights Management usagehttps://docs.microsoft.com/rights-management/deploy-use/log-analyze-usage (https://docs.microsoft.com/rights-management/deploy-use/log-analyze-usage) on the Microsoft documentation site.

## EXAMPLES

### Example 1: Get usage log feature
```
PS C:\>Get-AadrmUsageLogFeature
True
```

This command gets whether the usage log feature is enabled.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Disable-AadrmUsageLogFeature](.\Disable-AadrmUsageLogFeature.md)

[Enable-AadrmUsageLogFeature](.\Enable-AadrmUsageLogFeature.md)


