---
external help file: AIPService.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400619
schema: 2.0.0
ms.assetid: A3A194BD-D7B2-417F-902D-33D40BB3B332
---

# Get-AipServiceUsageLogStorageAccount

## SYNOPSIS
Gets the location for usage logs.

## SYNTAX

```
Get-AipServiceUsageLogStorageAccount [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceUsageLogStorageAccount** cmdlet gets the Azure storage location for usage logs for Azure Information Protection service.

You must use PowerShell to get this information; you cannot do this action by using a management portal.

This cmdlet should be used only if you have usage logs prior to the usage logging change in February 2016.
After this date, the only Windows PowerShell cmdlet that you need for AIP Service usage logging is the [Get-AipServiceUserLog](./Get-AipServiceUserLog.md) cmdlet.

For more information about usage logging, see [Logging and analyzing usage of the Azure Information Protection service](https://docs.microsoft.com/information-protection/deploy-use/log-analyze-usage).

## EXAMPLES

### Example 1: Get the log location
```
PS C:\>Get-AipServiceUsageLogStorageAccount
```

This command gets the location for your usage logs.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Get-AipServiceUserLog](./Get-AipServiceUserLog.md)

[Set-AipServiceUsageLogStorageAccount](./Set-AipServiceUsageLogStorageAccount.md)

[Logging and analyzing usage of the Azure Information Protection service](https://docs.microsoft.com/information-protection/deploy-use/log-analyze-usage)
