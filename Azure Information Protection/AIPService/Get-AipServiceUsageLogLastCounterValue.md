---
external help file: Microsoft.RightsManagementServices.Online.Admin.PowerShell.dll-Help.xml
online version: http://go.microsoft.com/fwlink/?LinkId=400618
schema: 2.0.0
ms.assetid: BE5835E8-F97C-4F0E-8B2A-6698819D61CD
---

# Get-AipServiceUsageLogLastCounterValue

## SYNOPSIS
Gets the last counter value for the usage log.

## SYNTAX

```
Get-AipServiceUsageLogLastCounterValue [<CommonParameters>]
```

## DESCRIPTION
The **Get-AipServiceUsageLogLastCounterValue** cmdlet gets the last counter value for the usage log.

You must use PowerShell to get this information; you cannot do this action by using a management portal.

This cmdlet should be used only if you have usage logs prior to the usage logging change in February 2016.
After this date, the only Windows PowerShell cmdlet that you need for AIP Service usage logging is [Get-AipServiceUserLog](./Get-AipServiceUserLog.md).

For more information about usage logging, see [Logging and analyzing usage of the Azure Information Protection service](https://docs.microsoft.com/information-protection/deploy-use/log-analyze-usage).

## EXAMPLES

### Example 1: Get the last counter value
```
PS C:\>Get-AipServiceUsageLogLastCounterValue
```

This command gets the last counter value for the usage log for your organization.

## PARAMETERS

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

[Enable-AipServiceUsageLogFeature](./Enable-AipServiceUsageLogFeature.md)

[Logging and analyzing usage of the Azure Information Protection service](https://docs.microsoft.com/information-protection/deploy-use/log-analyze-usage)
