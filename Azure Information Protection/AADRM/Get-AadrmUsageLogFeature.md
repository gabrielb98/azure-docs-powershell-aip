---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400617
schema: 2.0.0
ms.assetid: C63B5A33-75B8-43A4-83E2-F6AF477A5BBF
---

# Get-AadrmUsageLogFeature

## SYNOPSIS
Deprecated: Gets the status of legacy usage logging for Rights Management.

## SYNTAX

```
Get-AadrmUsageLogFeature [<CommonParameters>]
```

## DESCRIPTION
This cmdlet is now deprecated.

This cmdlet always returns **False** after the usage logging change in February 2016. After this date, usage logging is enabled automatically and the only Windows PowerShell cmdlet that you need for Azure RMS usage logging is [Get-AadrmUserLog](./Get-AadrmUserLog.md).

For more information about usage logging, see [Logging and analyzing usage of the Azure Rights Management service](/information-protection/deploy-use/log-analyze-usage).

## EXAMPLES

### Example 1: Get usage log feature
```
PS C:\>Get-AadrmUsageLogFeature
False
```

This command always returns False because this cmdlet is now deprecated.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AadrmUserLog](./Get-AadrmUserLog.md)

[Logging and analyzing usage of the Azure Rights Management service](/information-protection/deploy-use/log-analyze-usage)